---
layout: post
title:  "'PHP Nature' missing from 'Project Natures' in Aptana Studio 2.0"
date:   2010-01-13 22:50:00 +0000
tags: [ Web Development, PHP, Aptana ]
permalink: blog/php-nature-missing-project-natures-aptana-studio-20
---
For some reason, even though I have the PHP Development Tools (PDT) installed in Aptana Studio (2.0), I'm not able to select 'PHP nature' in the 'Project natures' of an imported project. I can start a new PHP Project which will have the 'PHP nature' selected as primary nature, but this doesn't even appear as an option in imported projects. The only two natures that are available are 'Remote Nature' and 'Web Nature'. The 'PHP nature' adds some really useful functions, like grouping my @todos into Aptana's Tasks view and also other handy things like auto-completing PHP docblocks.

To get the 'PHP nature' associated with your imported project you can manually edit the .project file which Aptana creates in your imported project directory so that it contains the 'PHP nature'. To do this, add the following code between the <natures> tags in your .project file:

```xml
<natures>
   <nature>org.eclipse.php.core.PHPNature</nature>     
</natures>
```

You may need to re-load Aptana to refresh the project but you should now find that your imported project has a primary 'PHP nature' set.

Note: Please do this at your own risk; although it worked fine for me I don't know if it will cause any side effects to the project or Aptana.