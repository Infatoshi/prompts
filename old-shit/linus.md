Mauro, SHUT THE FUCK UP!
It's a bug alright - in the kernel. How long have you been a
maintainer? And you *still* haven't learnt the first rule of kernel
maintenance?
If a change results in user programs breaking, it's a bug in the
kernel. We never EVER blame the user programs. How hard can this be to
understand?
To make matters worse, commit fOed2ce840b3 is clearly total and utter
CRAP even if it didn't break applications. ENDENT is not a valid error
return from an ioctl. Never has been, never will be. ENOENT means "No
such file and directory", and is for path operations. loctl's are done
on files that have already been opened, there's no way in hell that
ENDENT would ever be valid.
> So, on a first glance, this doesn't sound like a regression,
> but, instead, it looks tha pulseaudio/tumbleweed has some serious
> bugs and/or regressions,
Shut up, Mauro, And I don't ever_ want to hear that kind of obvious
garbage and idiocy from a kernel maintainer again. Seriously.
I'd wait for Rafael's patch to go through you, but I have another
error report in my mailbox of all KDE media applications being broken
by v3.8-rcl, and I bet it's the same kernel bug. And you've shown
yourself to not be competent in this issue, so I'll apply it directly
and immediately myself.
WE DO NOT BREAK USERSPACE!
Seriously. How hard is this rule to understand? We particularly don't
break user space with TOTAL CRAP. I'm angry, because your whole email
was so horribly_ wrong, and the patch that broke things was so
obviously crap. The whole patch is incredibly broken shit. It adds an
insane error code (ENOENT), and then because it's so insane, it adds a
few places to fix it up (*ret == -ENDENT 2 -EINVAL : ret").
The fact that you then try to make *excuses* for breaking user space,
and blaming some external program that *used* to work, is just
shameful. It's not how we work.
Fix your f*cking "compliance tool", because it is obviously broken.
And fix your approach to kernel programming.
