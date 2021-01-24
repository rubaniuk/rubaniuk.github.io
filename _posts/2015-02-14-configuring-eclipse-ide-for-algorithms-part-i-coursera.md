---
# id: 365
title: Configuring Eclipse IDE for Algorithms, Part I (Coursera)
date: 2015-02-14T18:45:49-08:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=365
# permalink: /?p=365
categories:
  - Coursera
  - Java
  - Software Development
---
<p style="text-align: left;">
  Coursera is offering great algorithmic courses <a title="Algorithms, Part I" href="https://www.coursera.org/course/algs4partI" target="_blank">Algorithms, Part I</a> and <a title="Algorithms, Part II" href="https://www.coursera.org/course/algs4partI" target="_blank">Part II</a> by Robert Sedgewick. The only problem with them is Dr. Java IDE they recommend. It is free, usable but completely impractical when it comes to debugging.  I&#8217;ve configured Eclipse IDE and my productivity increased significantly, especially when it comes to debugging.
</p>

<p style="text-align: left;">
  Here is how to configure Eclipse on Windows machine for Algorithms, Part I/part II:
</p>

<li style="text-align: left;">
  Uninstall any instances of Java from your machine
</li>
<li style="text-align: left;">
  Follow step 0 from <a title="Hello World in Java on Windows" href="http://algs4.cs.princeton.edu/windows/" target="_blank">http://algs4.cs.princeton.edu/windows/</a> to install <a title="algs4.exe" href="http://algs4.cs.princeton.edu/windows/algs4.exe" target="_blank">algs4.exe</a> <ul>
    <li>
      only follow step 0, skip the rest as we will use Eclipse instead of Dr. Java
    </li>
  </ul>
</li>

<li style="text-align: left;">
  Download <a title="stdlib.jar" href="http://algs4.cs.princeton.edu/code/stdlib.jar" target="_blank">stdlib.jar</a> and <a title="algs4.jar" href="http://algs4.cs.princeton.edu/code/algs4.jar" target="_blank">algs4.jar</a> to permanent folder
</li>
<li style="text-align: left;">
  Download <a title="Eclipse IDE for Java Developers" href="http://www.eclipse.org/downloads/" target="_blank">Eclipse IDE for Java Developers</a> <ul>
    <li>
      At the time of this blog post I had Eclipse Luna SR1 4.4.1 on my machine
    </li>
  </ul>
</li>

  1. Follow instructions in <a title="eclipse.pdf" href="http://www.cs.princeton.edu/~elancast/labta/eclipse.pdf" target="_blank">eclipse.pdf</a> to configure Eclipse. 
    <li style="text-align: left;">
      The instructions are long and little tedious but well worth it
    </li>
    <li style="text-align: left;">
      Here&#8217;s how you create a User Library in Eclipse: go to Window > Preferences > Java > Build Path > User Libraries, create New library and add<strong><em> algs4.jar</em></strong> and <em><strong>stdlib.jar</strong></em> from step 3 (I called it Coursera): <a href="http://www.rubaniuk.com/wp-content/uploads/2015/02/0UserLibraries.png"><img loading="lazy" class="aligncenter size-full wp-image-371" src="http://www.rubaniuk.com/wp-content/uploads/2015/02/0UserLibraries.png" alt="0UserLibraries" width="702" height="559" srcset="https://www.rubaniuk.com/wp-content/uploads/2015/02/0UserLibraries.png 702w, https://www.rubaniuk.com/wp-content/uploads/2015/02/0UserLibraries-300x238.png 300w, https://www.rubaniuk.com/wp-content/uploads/2015/02/0UserLibraries-624x496.png 624w" sizes="(max-width: 702px) 100vw, 702px" /></a>
    </li>
      * Whenever you create a new Java project you need to add newly created user library : right click on project, Build Path > Add Libraries [<img loading="lazy" class="aligncenter size-full wp-image-372" src="http://www.rubaniuk.com/wp-content/uploads/2015/02/1AddLibrary.png" alt="1AddLibrary" width="525" height="508" srcset="https://www.rubaniuk.com/wp-content/uploads/2015/02/1AddLibrary.png 525w, https://www.rubaniuk.com/wp-content/uploads/2015/02/1AddLibrary-300x290.png 300w" sizes="(max-width: 525px) 100vw, 525px" />](http://www.rubaniuk.com/wp-content/uploads/2015/02/1AddLibrary.png) [<img loading="lazy" class="aligncenter size-full wp-image-373" src="http://www.rubaniuk.com/wp-content/uploads/2015/02/2AddLibrary.png" alt="2AddLibrary" width="525" height="508" srcset="https://www.rubaniuk.com/wp-content/uploads/2015/02/2AddLibrary.png 525w, https://www.rubaniuk.com/wp-content/uploads/2015/02/2AddLibrary-300x290.png 300w" sizes="(max-width: 525px) 100vw, 525px" />](http://www.rubaniuk.com/wp-content/uploads/2015/02/2AddLibrary.png)
      * Here&#8217;s what your Java project in Eclipse will look like after adding this library:[<img loading="lazy" class="aligncenter size-full wp-image-374" src="http://www.rubaniuk.com/wp-content/uploads/2015/02/3Project.png" alt="3Project" width="633" height="531" srcset="https://www.rubaniuk.com/wp-content/uploads/2015/02/3Project.png 633w, https://www.rubaniuk.com/wp-content/uploads/2015/02/3Project-300x251.png 300w, https://www.rubaniuk.com/wp-content/uploads/2015/02/3Project-624x523.png 624w" sizes="(max-width: 633px) 100vw, 633px" />](http://www.rubaniuk.com/wp-content/uploads/2015/02/3Project.png)

Eclipse worked well for me and as I mentioned previously increased my productivity which made studying fun again.

Good luck and let me know if you have questions!