# utl-example-of-ods-crosstab-output-table-with-mean-and-std-using_proc-report
Unlike the tabulate static printout, this solution produces a 'ods' table.
    Example of ods crosstab output table with mean and std using_proc report

    Unlike the tabulate static printout, this solution produces a 'ods' table.

    I have updated the macro 'utl_odsrpt' to eliminate possible
    'file in use' errors'.

    Original ODS algorithm by
    Bartosz Jablonski

    yabwon@gmail.com
    github
    https://tinyurl.com/y73jpvx8
    https://github.com/rogerjdeangelis/utl-example-of-ods-crosstab-output-table-with-mean-and-std-using_proc-report

    Macro on end and in

    macros
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories


    SAS Forum
    https://tinyurl.com/y7ego6ag
    https://communities.sas.com/t5/Statistical-Procedures/Overall-means/m-p/642176

    SOAPBOXON
      proc report is an amazing piece of software
      It can sort, transpose and summarize all at once and it is multi-threaded.
      I just wish it wouls honor ODS output tables.
    SOAPBOX OFF

    *_                   _
    (_)_ __  _ __  _   _| |_
    | | '_ \| '_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    ;

    DATA have;
    INPUT ID Veld BCS Sex Month Age @@;
    cards4;
    1 2 3 2 1 1 2 2 3 1 1 1 3 2 3 2 1 1 4 2 3 2 1 1 5 2 3 2 1 1 6 2 3 2 1 1
    7 2 3 2 1 1 8 2 3 1 1 2 9 2 3 1 1 2 10 2 3 2 1 2 11 2 3 1 1 2 12 2 3 2 1
    2 13 2 3 2 1 2 14 2 3 2 1 2 15 2 3 2 1 2 16 2 3 2 1 2 17 2 3 2 1 1 18 2
    3 1 1 2 19 2 3 1 1 2 20 2 1 1 1 1 21 2 2 1 1 3 22 2 4 1 1 3 23 2 3 1 1 3
    24 2 3 2 1 3 25 1 3 1 1 2 26 1 2 1 1 2 27 1 2 1 1 2 28 1 3 2 1 2 29 1 2
    1 1 3 30 1 3 2 1 2 31 1 3 2 1 2 32 1 2 1 1 4 33 1 3 1 1 4 34 1 3 2 1 4
    35 1 3 2 1 4 36 1 3 1 1 3 37 1 3 2 1 2 38 1 2 2 1 2 39 1 3 1 1 2 40 1 3
    2 1 1 41 1 3 1 1 2 42 1 3 1 1 2 43 1 3 1 1 1 44 1 2 2 1 1 45 1 4 2 1 1
    46 1 3 1 1 2 47 1 3 1 1 1 48 1 3 2 1 2 49 1 3 1 1 2 50 1 3 2 1 2 51 1 4
    2 1 2 52 1 4 1 1 2 53 1 4 2 1 2 54 1 3 2 1 2 55 1 3 2 1 2 56 1 3 2 1 2
    57 1 3 2 2 2 58 1 2 2 2 2 59 1 3 1 2 2 60 1 3 2 2 2 61 1 3 1 2 2 62 1 3
    1 2 1 63 1 3 1 2 2 64 1 2 2 2 1 65 1 4 2 2 2 66 1 3 1 2 2 67 1 3 1 2 2
    68 1 3 2 2 2 69 1 3 1 2 2 70 1 3 2 2 2 71 1 4 2 2 2 72 1 4 1 2 2 73 1 4
    2 2 2 74 1 3 2 2 2 75 1 3 2 2 2 76 1 3 2 2 2 77 1 3 1 2 3 78 1 2 1 2 2
    79 1 2 1 2 3 80 1 3 2 2 2 81 1 2 1 2 4 82 2 3 2 2 2 83 2 3 1 2 2 84 2 3
    2 2 1 85 2 3 2 2 2 86 2 3 2 2 2 87 2 3 2 2 1 88 2 3 2 2 1 89 2 3 1 2 2
    90 2 3 1 2 2 91 2 3 2 2 2 92 2 3 1 2 2 93 2 3 2 2 2 94 2 3 2 2 2 95 2 3
    2 2 2 96 2 3 2 2 2 97 2 3 2 2 2 98 2 3 2 2 2 99 2 3 1 2 2 100 2 3 1 2 1
    101 1 3 1 3 4 102 1 3 1 3 4 103 1 2 1 3 3 104 1 3 2 3 2 105 1 3 2 3 2
    106 1 3 2 3 2 107 1 2 2 3 2 108 1 3 1 3 4 109 1 3 1 3 2 110 1 3 2 3 2
    111 1 2 1 3 2 112 1 2 2 3 2 113 1 3 2 3 2 114 1 3 2 3 2 115 1 2 1 3 2
    116 1 3 2 3 2 117 1 2 1 3 1 118 1 3 2 3 2 119 1 3 2 3 2 120 1 3 2 3 2
    121 1 3 2 3 2 122 1 2 2 3 2 123 1 3 1 3 2 124 1 2 2 3 2 125 1 3 1 3 2
    126 1 3 1 3 2 127 1 3 2 3 2 128 1 3 1 3 2 129 1 3 2 3 4 130 1 3 2 3 1
    131 1 3 2 3 4 132 1 3 1 3 3 133 1 3 2 3 3 134 1 3 1 3 3 135 1 2 2 3 2
    136 1 2 1 3 2 137 1 3 1 3 2 138 1 2 1 3 3 139 1 3 1 3 2 140 1 3 2 3 2
    141 1 2 1 3 2 142 1 3 1 3 4 143 1 3 1 3 3 144 1 3 2 3 4 145 1 3 1 3 4
    146 1 3 1 3 2 147 1 2 2 3 2 148 1 2 1 3 2 149 1 2 1 3 2 150 2 2 1 3 2
    151 2 3 1 3 2 152 2 2 2 3 2 153 2 3 2 3 2 154 2 3 2 3 2 155 2 2 2 3 2
    156 2 3 2 3 2 157 2 2 2 3 2 158 2 2 1 3 2 159 2 3 2 3 2 160 2 3 2 3 2
    161 2 3 1 3 3 162 2 3 1 3 3 163 2 3 2 3 3 164 2 3 2 3 3 165 2 3 2 3 3
    166 2 3 1 3 3 167 2 3 2 3 3 168 2 4 2 3 3 169 2 4 1 3 4 170 2 3 2 3 4
    171 2 3 1 3 2 172 2 3 2 3 2 173 2 2 1 3 2 174 2 2 2 3 2 175 2 3 2 3 2
    176 2 3 2 3 2 177 2 2 1 3 2 178 2 3 2 3 2 179 2 2 1 3 1 180 2 3 2 3 2
    181 2 3 2 3 2 182 2 3 2 3 2 183 2 3 2 3 2 184 2 2 2 3 2 185 2 3 1 3 2
    186 2 2 2 3 2 187 2 3 1 3 2 188 2 3 1 3 2 189 2 3 2 3 2 190 2 3 1 3 2
    191 1 3 1 4 1 192 1 3 1 4 1 193 1 2 2 4 2 194 1 2 2 4 2 195 1 3 1 4 2
    196 1 3 2 4 1 197 1 2 2 4 2 198 1 3 1 4 1 199 1 3 2 4 2 200 1 3 1 4 2
    201 1 3 2 4 2 202 1 3 1 4 2 203 1 2 2 4 1 204 1 3 1 4 1 205 1 3 1 4 2
    206 1 2 1 4 4 207 1 3 1 4 3 208 1 2 1 4 3 209 1 2 2 4 3 210 1 3 1 4 2
    211 1 2 2 4 1 212 1 3 2 4 4 213 1 3 1 4 4 214 1 3 2 4 4 215 1 3 2 4 3
    216 1 3 2 4 2 217 1 2 2 4 2 218 1 3 1 4 2 219 1 3 1 4 2 220 1 3 1 4 2
    221 1 2 2 4 2 222 1 4 2 4 2 223 1 3 2 4 3 224 1 3 1 4 2 225 1 3 1 4 2
    226 1 3 2 4 3 227 2 3 2 4 3 228 2 3 2 4 2 229 2 3 1 4 3 230 2 3 1 4 3
    231 2 3 1 4 3 232 2 3 2 4 3 233 2 3 2 4 3 234 2 3 1 4 3 235 2 3 2 4 3
    236 2 3 1 4 3 237 2 3 2 4 3 238 2 3 1 4 3 239 2 3 1 4 3 240 2 4 2 4 3
    241 2 4 1 4 3 242 2 3 2 4 3 243 2 4 2 4 3 244 2 3 2 4 3 245 2 3 2 4 3
    246 2 3 1 5 3 247 2 4 2 5 3 248 2 3 2 5 3 249 2 4 1 5 3 250 2 3 1 5 3
    251 2 3 2 5 3 252 2 4 2 5 3 253 2 3 2 5 3 254 2 4 1 5 4 255 2 3 2 5 3
    256 2 4 1 5 4 257 2 3 2 5 4 258 2 4 2 5 3 259 2 3 2 5 3 260 2 4 1 5 3
    261 2 4 2 5 4 262 2 3 1 5 2 263 2 3 1 5 4 264 2 3 2 5 4 265 2 3 1 5 4
    266 2 4 2 5 3 267 2 3 1 5 4 268 2 3 1 5 4 269 2 4 2 5 3 270 2 3 2 5 4
    271 2 3 1 5 4 272 2 4 2 5 3 273 2 4 2 5 3 274 2 3 2 5 3 275 2 3 1 5 3
    276 2 3 1 5 2 277 2 3 2 5 4 278 2 3 1 5 3 279 2 3 2 5 3 280 2 3 2 5 2
    281 2 3 1 5 4 282 2 3 1 5 3 283 2 3 2 5 3 284 2 3 1 5 4 285 2 3 1 5 3
    286 2 4 1 5 4 287 1 3 2 5 1 288 1 3 1 5 1 289 1 3 2 5 1 290 1 3 2 5 2
    291 1 3 2 5 2 292 1 3 1 5 2 293 1 4 2 5 2 294 1 3 2 5 2 295 1 3 2 5 2
    296 1 3 1 5 3 297 1 3 1 5 2 298 1 3 2 5 1 299 1 3 1 5 1 300 1 3 2 5 1
    301 1 3 2 5 1 302 1 3 2 5 2 303 1 3 2 5 2 304 1 3 2 5 1 305 1 4 1 5 1
    306 1 3 1 5 1 307 1 3 2 5 4 308 1 3 1 5 1 309 1 3 2 5 4
    ;;;;
    run;quit;

    *            _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| '_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    ;

    WORK.WANT total obs=4

      AGE          JAN              FEB              MAR              APR              MAY

      0-4     1.6 +/- 0.13b    1.7 +/- 0.21b    1.3 +/- 0.33b    1.0 +/- 0.00b    1.0 +/- 0.00b
      5-8     1.3 +/- 0.09b    1.4 +/- 0.08b    1.5 +/- 0.06b    1.1 +/- 0.05b    1.3 +/- 0.13b
      9-12    1.7 +/- 0.21b    1.0 +/- 0.00b    1.6 +/- 0.14b    1.8 +/- 0.09b    2.0 +/- 0.04b
      >13     1.0 +/- 0.00b    1.0 +/- .b       1.2 +/- 0.13b    1.0 +/- 0.00b    1.9 +/- 0.08b


    *
     _ __  _ __ ___   ___ ___  ___ ___
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    ;


    proc format;
    value ageRng
      1 = "0-4"
      2 = "5-8"
      3 = "9-12"
      4 = ">13"
    ;


    %utl_odsrpt(setup);
    proc report  data=have nowd missing noheader box formchar='|';
    title '|Age|AvgJan|StdJan|AvgFeb|StdFeb|AvgMar|StdMar|AvgAPR|StdApr|AvgMay|StdMay|';
    cols age month, (veld veld=stnerr);
    format age agerng. month mth.;
    define age    /  group format=ageRng.;
    define month  /  across order=data;   /* NOTE ORDER=DATA */
    define veld      /  analysis mean;
    define stnerr    /  analysis stderr;
    run;quit;
    %utl_odsrpt(outdsn=havTbl );

    /* intermediate result
    WORKHAVTBL total obs=4

      AGE      AVGJAN     STDJAN     AVGFEB     STDFEB     AVGMAR     STDMAR    AVGAPR     STDAPR      AVGMAY     STDMAY

      0-4     1.64286    0.13289    1.66667    0.21082    1.33333    0.33333     1.00     0.000000    1.00000    0.00000
      5-8     1.34375    0.08531    1.42857    0.08487    1.47619    0.06343     1.05     0.050000    1.25000    0.13056
      9-12    1.66667    0.21082    1.00000    0.00000    1.57143    0.13725     1.75     0.090289    1.95833    0.04167
      >13     1.00000    0.00000    1.00000     .         1.20000    0.13333     1.00     0.000000    1.88235    0.08055
    */

    data want;
      set havTbl;
      array avgs avg:;
      array stds std:;
      array avgStd $32 JAN FEB MAR APR MAY;
      do over avgs;
         avgStd = catx(" ",put(avgs,5.1),'+/-',cats(put(stds,5.2),'b'));
      end;
      drop avg: std:;
    run;quit;

    *
     _ __ ___   __ _  ___ _ __ ___
    | '_ ` _ \ / _` |/ __| '__/ _ \
    | | | | | | (_| | (__| | | (_) |
    |_| |_| |_|\__,_|\___|_|  \___/

    ;


    %macro utl_odsrpt(outdsn);


       %if %qupcase(&outdsn)=SETUP %then %do;

            %put @@@@ &=sysindex.;

            %let _tmp1_=a&sysindex.;

            %put xxxx &=_tmp1_;

            filename &_tmp1_ clear;  * just in case;

            %utlfkil(%sysfunc(pathname(work))/&_tmp1_..txt);

            filename &_tmp1_ "%sysfunc(pathname(work))/&_tmp1_..txt";

            %let _ps_= %sysfunc(getoption(ps));
            %let _fc_= %sysfunc(getoption(formchar));

            OPTIONS ls=max ps=32756  FORMCHAR='|'  nodate nocenter;

            title; footnote;

            proc printto print=&_tmp1_;
            run;quit;

       %end;
       %else %do;

            /* %let outdsn=tst;  */
            %put @@@ &=sysindex.;

            %let _tmp2_=b&sysindex.;
            %let _tmp1_=a%eval(&sysindex - 2);

            %put xxxx  &=_tmp1_;
            %put xxxx  &=_tmp2_;

            proc printto;
            run;quit;

            filename &_tmp2_ clear;

            %utlfkil(%sysfunc(pathname(work))/&_tmp2_.txt);

            proc datasets lib=work nolist;  *just in case;
             delete &outdsn;
            run;quit;

            filename &_tmp2_ "%sysfunc(pathname(work))/&_tmp2_.txt";

            data _null_;
              infile &_tmp1_ length=l;
              input lyn $varying32756. l;
              if countc(lyn,'|')>1;
              lyn=compress(lyn);
              putlog lyn;
              file &_tmp2_;
              put lyn;
            run;quit;

            proc import
               datafile=&_tmp2_
               dbms=dlm
               out=&outdsn(drop=VAR:)
               replace;
               delimiter='|';
               getnames=yes;
            run;quit;

            filename &_tmp1_ clear;
            filename &_tmp2_ clear;

            %utlfkil(%sysfunc(pathname(work))/&_tmp1_.txt);
            %utlfkil(%sysfunc(pathname(work))/&_tmp2_.txt);

       %end;

    %mend utl_odsrpt;


