# CBT770
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 770 is from Deru Sudibyo and contains a free z/OS event   *   FILE 770
//*           management system, which can be used for automation.  *   FILE 770
//*           Control of the system is from REXX statements, using  *   FILE 770
//*           a REXX function package which is supplied together    *   FILE 770
//*           with this system.                                     *   FILE 770
//*                                                                 *   FILE 770
//*           email:  Deru Sudibyo <deru.sudibyo@gmail.com>         *   FILE 770
//*                                                                 *   FILE 770
//*     Note:  The member CBTSETUP is not necessary in this         *   FILE 770
//*            pds, but has been included because it is the work    *   FILE 770
//*            of the author, and it may be necessary in a future   *   FILE 770
//*            install process.                                     *   FILE 770
//*                                                                 *   FILE 770
//*     A description of this package follows:                      *   FILE 770
//*                                                                 *   FILE 770
//*     zCBT Automation Tools                                       *   FILE 770
//*     Copyright (c) 2006   Deru Sudibyo                           *   FILE 770
//*                                                                 *   FILE 770
//*     What is zCBT?                                               *   FILE 770
//*                                                                 *   FILE 770
//*     zCBT is a miniature of (my commercial package) zJOS.        *   FILE 770
//*     zCBT is the simplest solution for z/OS system event         *   FILE 770
//*     management at no cost.  You don't need special skill to     *   FILE 770
//*     automate your system using zCBT. Once zCBT is properly      *   FILE 770
//*     setup, you will very able to manage your system events      *   FILE 770
//*     using very simple rexx scripting.  All you need is rexx     *   FILE 770
//*     skill.                                                      *   FILE 770
//*                                                                 *   FILE 770
//*     zCBT is a combination of subsystem functions and resource   *   FILE 770
//*     manager which runs on z/OS as a subsystem, instead of an    *   FILE 770
//*     address space.  zCBT subsystem supports 5 types of          *   FILE 770
//*     events:                                                     *   FILE 770
//*                                                                 *   FILE 770
//*     Messages (MSG) events for both WTO and WTOR. Message is     *   FILE 770
//*     trapped before sent to console, hence you can optionally    *   FILE 770
//*     suppress it. By trapping substring of message text, you     *   FILE 770
//*     can do several actions.  For WTOR message, you can reply    *   FILE 770
//*     it.                                                         *   FILE 770
//*                                                                 *   FILE 770
//*     Command (CMD) events.  Command is trapped before sent       *   FILE 770
//*     console, hence you can optionally suppress it.  This is     *   FILE 770
//*     an opportunity for you to have your own console             *   FILE 770
//*     commands.  By preparing rexx routine to trap certain        *   FILE 770
//*     command verbs (regardless they are valid commands) and      *   FILE 770
//*     their associated actions, you will have your own            *   FILE 770
//*     commands.                                                   *   FILE 770
//*                                                                 *   FILE 770
//*     End-of-jobstep (EOS) events for both jobs and STCs.         *   FILE 770
//*     EOS event is trapped at almost the time of its              *   FILE 770
//*     occurrence and reporting condition codes. If you are a      *   FILE 770
//*     smart programmer, by using zCBT you can develop your        *   FILE 770
//*     own scheduler in rexx language.                             *   FILE 770
//*                                                                 *   FILE 770
//*     End-of-job (EOJ) events for jobs and STCs.  EOJ event       *   FILE 770
//*     is simulated from all related EOS previously occurred.      *   FILE 770
//*     Hence, there is a short time delay (less than 1 sec).       *   FILE 770
//*                                                                 *   FILE 770
//*     Time-of-day (TOD) events.  TOD is very common event         *   FILE 770
//*     people can trap.  Internally it just STIMER or STIMERM      *   FILE 770
//*     macro which doesn't need authorization as privileged        *   FILE 770
//*     routine.  Since rexx able to obtain date and time, zCBT     *   FILE 770
//*     only support TOD time event for both clock and interval     *   FILE 770
//*     time.                                                       *   FILE 770
//*                                                                 *   FILE 770
//*     The way zCBT subsystem supports system automation is by     *   FILE 770
//*     providing some rexx functions.  Request regarding which     *   FILE 770
//*     event you want to trap is sent to zCBT as function          *   FILE 770
//*     arguments.  Trapped event information is then returned      *   FILE 770
//*     to you as result value of the issued function.  Although    *   FILE 770
//*     rexx is executed synchronously, you can however, trap       *   FILE 770
//*     multiple events within a single rexx program.  CBTIVP       *   FILE 770
//*     member of REXXLIB dataset gives you example how to          *   FILE 770
//*     handle multiple events.                                     *   FILE 770
//*                                                                 *   FILE 770
//*     Your rexx program can run on TSO TMP session, TSO batch     *   FILE 770
//*     or non-TSO job.  To run CBTIVP, you can start JCBTEST1      *   FILE 770
//*     member of JCLLIB as either normal STC or under MSTR         *   FILE 770
//*     subsystem.   If you need zCBT to automate your system       *   FILE 770
//*     startup, you must run your rexx program as STC under        *   FILE 770
//*     MSTR subsystem.                                             *   FILE 770
//*                                                                 *   FILE 770
//*     zCBT Supported Rexx Functions                               *   FILE 770
//*                                                                 *   FILE 770
//*     You can easily handle 5 types of events, message,           *   FILE 770
//*     command, end-of-jobstep (EOS), end-of-job (EOJ) and         *   FILE 770
//*     time-of-day (TOD) by using ordinary rexx scripting or       *   FILE 770
//*     programming. To do so, zCBT provides 7 rexx functions,      *   FILE 770
//*     these are:                                                  *   FILE 770
//*                                                                 *   FILE 770
//*     cbcmd()                                                     *   FILE 770
//*     cbevent()                                                   *   FILE 770
//*     cbserver()                                                  *   FILE 770
//*     cbset()                                                     *   FILE 770
//*     cbwait()                                                    *   FILE 770
//*     cbwto()                                                     *   FILE 770
//*     cbwtor()                                                    *   FILE 770
//*                                                                 *   FILE 770
//*     See the internal documentation for explanations for         *   FILE 770
//*     each function:  members $DOCTXT (text) or @DOC (MS word).   *   FILE 770
//*                                                                 *   FILE 770
```
