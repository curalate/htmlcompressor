This commit contains a forked version of the HtmlCompressor Java library available
here: https://code.google.com/p/htmlcompressor/.

This fork fixes an issue that causes YUICompressor to fail to run on Tomcat.  Essentially
the Yahoo developers who developed this library decided to overwrite a subset of files in
the Rhino JS engine (http://www.julienlecomte.net/blog/2008/10/80/).  This ends up
breaking binary compatibility with the Rhino JS jar.

Our fix here is to:
- Pull the Rhino source code into this repository.
- Namespace the Rhino source code into a separate package.  This will ensure this modified
version of Rhino can co-exist with another version of Rhino used elsewhere in the system.
- Update the htmlcompressor code to use the new namespaced packages.

Note that the namespaced version of Rhino + yuicompressor is pulled from
https://github.com/timothy-kim/yuicompressor

