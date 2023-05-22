---
layout: page
title: "IDPF (Ideal driver platform)"
date: 2018-03-18 13:44
comments: true
sharing: true
footer: true
---
IDPF design and develop as printer driver for fujixerox printer devices on Windows os after Windows XP(including Windows XP, Vista, 7, server2008). The whole project splits two parts, the plantform part is focus on new feature development. And product part focus on create the collection for the requirements of the real printer device. That means the plantform contains all features of the printers and production chose some features.

{% img /images/uni.png %}

As shown as the figure, IDPF is designed based on Microsoft Universal Printer Driver, and the figure shows the structure of the unidiver. Microsoft create a whole workflow from UI to spooler service(output). And Microsoft gives two entries for the user to customize their own driver, UI plug-in module and Render plug-in module. One is define the UI pages and another is define the output contents. Both modules defines COM interface for user and lots of API for the driver functions(refer to [IPrintOemUI](https://docs.microsoft.com/en-us/windows-hardware/drivers/print/introduction-to-user-interface-plug-ins) and [IPrintOemUni](https://docs.microsoft.com/en-us/windows-hardware/drivers/print/iprintoemuni-com-interface)).

For us, we design UI plugin with DXD(one script like json), and we make every kind of element(e.g. button, label, textbox, checkbox, radiobutton...) as a entry of the script, then we dynaimicly run the UI with the script paser. And rendering plugin is mainly moved from the old driver rendering engine which renders the documents or pictures to the pwl (kind of page description language like pcl), and makes a header of commands based on the printer setttings in the output file. The rendering engine of old driver system is implemented by native C, so we implemented the COM object and make connection with the old  rendering engine.

The chanllege of the project is make a balance between flexibility and performance, the platform needs to map to hundreds of products. They have different UI and features. And we also create another script to handle the constraints of UI (e.g. if feature 1 is selected, feature 2 should be disabled). When the elements of UI become huge, there are conficts between constraints. And of course loading and searching of script tree will become slow. We make some solutions to improve the performance, e.g. create index map for the most used features and constraints, and improve the searching algorithm as hybird one. These solutions gives big improvements of the system.

For me, this project is the first large business system which is programming closing to the windows os kernel. It makes me learn lots about Windows Kernel Programming and COM framework at that time. And it also improve my software design knowledge and c++ expeirence.
