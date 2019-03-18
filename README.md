# osolmaz.github.io

##### What I had to do for initial configuration

- Apparently, you need to provide your site's url as the `baseurl` variable in
`_config.yaml`, or the static generator does not generate valid references.

Look at the answer by @mjswensen in
[this](https://github.com/jekyll/jekyll/issues/332) issue:

> I finally figured out the trick, if you're looking for a solution with the standard URL for GitHub Pages (`username.github.io/project-name/`). Here's what to do:
>
> In `_config.yml`, set the `baseurl` option to `/project-name` -- note the leading slash and the absence of a trailing slash.
> Now you'll need to change the way you do links in your templates and posts, in the following two ways:
>
> When referencing JS or CSS files, do it like this: `{{ site.baseurl }}/path/to/css.css` -- note the slash immediately following the variable (just before "path").
>
> When doing permalinks or internal links, do it like this: `{{ site.baseurl }}{{ post.url }}` -- note that there is no slash between the two variables.
> Finally, if you'd like to preview your site before committing/deploying using `jekyll serve`, be sure to pass an empty string to the --baseurl option, so that you can view everything at `localhost:4000` normally (without `/project-name` getting in there to muck everything up): `jekyll serve --baseurl ''`
>
> This way you can preview your site locally from the site root on localhost, but when GitHub generates your pages from the gh-pages branch all the URLs will start with `/project-name` and resolve properly.

For me, putting

    baseurl: "http://osolmaz.github.io"

in `_config.yaml` worked out.

##### Running as a local server

    jekyll serve --baseurl --watch
