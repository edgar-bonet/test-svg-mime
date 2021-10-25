Below are two SVG images. The first one contains the text “JavaScript is
OFF”, together with a script that changes “OFF” to “ON”. The second one
has no JavaScript:

![(this is the alt text of the first image)](image.svg)
![(this is the alt text of the second image)](image-nojs.svg)

On GitHub, both images are displayed, served as image/svg+xml from a
different domain (raw.githubusercontent.com) with the header
“Content-Security-Policy: default-src 'none'; style-src 'unsafe-inline';
sandbox”. Neither Firefox nor Chromium execute the script, even if the
image is opened alone, in a new tab.

Gitea has the same behavior, except that the images are served from the
same domain. The script is not executed, presumably thanks to the
Content-Security-Policy header.

On Gogs, clickable alt texts are displayed instead of the images. Unlike
Firefox, Chromium also displays broken-image icons alongside the alt
texts.

When clicking on the images, Gitea displays the raw images. GitHub
instead displays a “blob” page in “rendered” view. This page contains an
iframe served from render.githubusercontent.com, with the image
included, as before, from raw.githubusercontent.com. That blob page has
buttons for switching between the rendered and source blob views, and a
link to the raw file from raw.githubusercontent.com.

When clicking on the alt texts, Gogs displays the raw source of the
images (the images served as text/plain).

Tests:

* [on github.com](https://github.com/edgar-bonet/test-svg-mime)
* [on try.gogs.io](https://try.gogs.io/edgar/test-svg-mime) (requires
  creating an account)
* [on try.gitea.io](https://try.gitea.io/edgar/test-svg-mime)

The issue has been reported:

* GitHub: [Fix relative SVG rendering](https://github.com/github/markup/issues/556)
* Gogs: [SVG images are served with wrong MIME type](https://github.com/gogits/gogs/issues/4553)
* Gitea: [Gitea can't render SVG files.](https://github.com/go-gitea/gitea/issues/1095)
* GitLab: [Breakage in displaying SVG in the same repository](https://gitlab.com/gitlab-org/gitlab-ce/issues/17276)
