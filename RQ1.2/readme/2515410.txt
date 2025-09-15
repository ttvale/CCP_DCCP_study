TextBlock
=========

Simple text ignore / discard system for Android. Lightweight, non-intrusive, and sexy.

Licensed under [GPLv3] (https://github.com/outerearthinteractive/TextBlock/blob/master/COPYING.markdown "License Info"), distributed on Android Market with advertising to support Outer Earth Interactive and future applications. Master branch will have no advertisements, so compile away.

If you find something wrong, use the issue tracker. If you can fix it yourself, submit a pull request. Same goes for desired features.

I'm making this because I have a few friends I wish to teach Android development to, and what better place to start than actually working on something.

I also keep getting annoying messages from Verizon.



Methodology of Workitude and Functionality 
==========================================

The application can be toggled to start on boot.

While running, it compares incoming SMS's against a blacklist. If the source number is on the blacklist, it disposes of the message gracefuly without notification. Statistics will be added later, and maybe even a silent collection box. All features will be enabled / disabled by preferences, of course.

This application should be very performance-friendly, it won't keep messages in memory or anything like that.


