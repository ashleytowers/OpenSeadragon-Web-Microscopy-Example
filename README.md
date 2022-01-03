OpenSeadragon-Web-Microscopy-Example
====================================

This repository contains a self contained demo of a converted Aperio SVS file running in OpenSeadragon that you can just extract to your web server and view in a browser.

If you want to create your own DZI files from Aperio SVS files then you can do the following:

Install VIPS
------------

The first step is to install VIPS. VIPS  is a command line image processing utility that is able to use OpenSlide and will handle the image conversion for us. To install it fire up a terminal and execute the following command:

  brew install https://raw.github.com/jcupitt/homebrew-science/3fda4568544a67743b2a880ad1c5f844b4ff3515/vips.rb --with-openslide

This will take quite a while as it builds and installs VIPS and all its dependencies. If you have any problems, the full [VIPS build/install instructions](http://www.vips.ecs.soton.ac.uk/index.php?title=Build_on_OS_X) are available on their Wiki.

The next step is to use VIPS to convert the SVS image in to a format that OpenSeadragon can understand.

Converting SVS to DZI
----------------------

To convert your SVS file to a DZI file execute the following command:

  vips dzsave /path/to/your/image.svs /path/to/output/directory

For example running the following:

  vips dzsave ~/mucocoele.svs ~/webMucocoele

Will create a file called mucocoele.dzi and a folder called mucocoele_files. Both of these are required.

NB if your source svs image is large this conversion can take a long time!

NB.2 if you receive a "VipsForeignLoad" error then you probably didn't include the "--with-openslide" parameter when installing VIPS. You'll need to brew uninstall it and rebuild including the parameter.

Change index.html
-----------------

To get your new files in to the web page you'll need to put them in a public folder and then change the "tileSources" parameter to point to the relative path of your new file.

A more comprehensive guide is available in this [blog post](http://www.ashleytowers.co.uk/publishing-aperio-svs-virtual-microscopy-images-to-the-web-using-vips-openslide-and-openseadragon/)

**Edit:** Wayback machine has a copy of the above post from my (long) defunct blog available [here](https://web.archive.org/web/20161028051758/http://www.ashleytowers.co.uk/publishing-aperio-svs-virtual-microscopy-images-to-the-web-using-vips-openslide-and-openseadragon/)
