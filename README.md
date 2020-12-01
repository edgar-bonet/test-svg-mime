Below are two SVG images. The first one contains the text “JavaScript is
OFF”, together with a script that changes “OFF” to “ON”. The second one
has no JavaScript:

![(this is the alt text of the first image)](image.svg)
![(this is the alt text of the second image)](image-nojs.svg)

On GitHub, both images are displayed, served from a different domain
(raw.githubusercontent.com). The first image has his JavaScript stripped
away. On Gogs and Gitea, the alt texts are displayed instead of the
images. On Gogs, both alt texts are clickable. On Gitea only the first
one is clickable. Unlike Firefox, Chromium also displays broken-image
icons alongside the alt texts.

When clicking on the alt texts, Gogs and Gitea display the raw source of
the images (the images served as text/plain). GitHub instead displays a
“blob” page in “rendered” view, with the image embedded as a data URL
from an iframe. Although the JavaScript has not been removed from the
first image, it is not interpreted by the browser. That blob page has
buttons for switching between the rendered and source blob views, and a
link to the raw file (served as text/plain from
raw.githubusercontent.com).

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
