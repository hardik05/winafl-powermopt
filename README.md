# WinAFL PowerMopt

WinAFL with mopt mutators and AFLFast power schedulers.

```
   Original AFL code written by Michal Zalewski <lcamtuf@google.com>

   Windows fork written and maintained by Ivan Fratric <ifratric@google.com>  
   
   Mopt and PowerSchedulers ported to winafl by Hardik Shah <hardik05@gmail.com>
   [hardik05](https://twitter.com/hardik05)
   
   Original Mopt mutators from: https://github.com/puppet-meteor/MOpt-AFL, based on the work of Chenyang Lyu, Shouling Ji, Chao Zhang, Yuwei Li, Wei-Han Lee, Yu Song and Raheem Beyah
   Orignal AFL Fast power schedulers from: https://github.com/mboehme/aflfast, based on the work of mboehme

   Original winafl read me: [ReadMe](https://github.com/googleprojectzero/winafl/blob/master/README.md)
   .
```
## Why another fork?
On windows we are limited in fuzzing capabilities, while there are lot of mods to original AFL, winafl is way behind in terms of latest AFL development. So I decided to use AFLFast power schedulers and AFL Mopt mutators to winafl. This is my mod to winafl. Note that these uses powerschedulers and mopt mutators from their original AFL releases and thus may not be up to date. if you can update this with the latest version then PR are most welcome!

## Using WinAFL and mOpt, PowerScheduler options

The command line for afl-fuzz on Windows is different than on Linux. Instead of:

```
%s [ afl options ] -- target_cmd_line
```

it now looks like this:

```
afl-fuzz [afl options] -- [instrumentation options] -- target_cmd_line
```

The following afl-fuzz options are supported:

```
  -i dir        - input directory with test cases
  -o dir        - output directory for fuzzer findings
  -t msec       - timeout for each run
  -s            - deliver sample via shared memory
  -D dir        - directory containing DynamoRIO binaries (drrun, drconfig)
  -w path       - path to winafl.dll
  -P            - use Intel PT tracing mode
  -Y            - enable the static instrumentation mode
  -f file       - location read by the fuzzed program
  -m limit      - memory limit for the target process
  -p            - persist DynamoRIO cache across target process restarts
  -c cpu        - the CPU to run the fuzzed program
  -d            - quick & dirty mode (skips deterministic steps)
  -n            - fuzz without instrumentation (dumb mode)
  -x dir        - optional fuzzer dictionary
  -I msec       - timeout for process initialization and first run
  -T text       - text banner to show on the screen
  -M \\ -S id   - distributed mode
  -C            - crash exploration mode (the peruvian rabbit thing)
  -l path       - a path to user-defined DLL for custom test cases processing
  -F schedule   - power scheuler(this is from AFLFast) - fast (default), coe, explore, lin, quad, or exploit
  -L            - This is from mOpt-AFL, time to enter pacemaker fuzzing mode. 
```
## F and L options are for powerscheule and mopt mutators respectivly. 
## MOpt mutators from: https://github.com/puppet-meteor/MOpt-AFL
## AFLFast powerschedulers from: https://github.com/mboehme/aflfast
##

Please refer to the original AFL documentation for more info on these flags.

To see the supported instrumentation flags, please refer to the documentation
on the specific instrumentation mode you are interested in.
