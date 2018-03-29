<img src="themes/hugo-lithium-theme/static/images/fakin_blog.png" alt="fakin_blog_logo" />

Blog on FAKIN project status 


## How to update the blog

### Step 1: Install blogdown package

```r

# Install the devtools package
if (! require("devtools")) {

  install.packages("devtools", repos = "https://cloud.r-project.org")
}

# Install the blogdown package
devtools::install_github("rstudio/blogdown")

# Install hugo
blogdown::install_hugo()
```

### Step 2: Create new knowledge post

Create a Rmarkdown post similar to **[2017-05-19-fakin-project-started.Rmd](content/post/2017-05-19-fakin-project-started.Rmd)** in directory ***content/post***.

### Step 3: Update the blog 

To do so run the following R code: 
```r

### Delete "public" folder (i.e. in case of older website builds)
unlink("public", recursive = TRUE)

### Build site
blogdown::build_site(local = FALSE)

### Copies files from public folder (please do not COMMIT!!) into docs 
### folder which is required to work for GITHUB (all changed content of 
### the docs folder needs to be committed to Github for the blog to be
### updated)
file.copy(from = "public/.", to = "docs", overwrite = TRUE, recursive = TRUE)

```

If completed finally commit (vit GIT/Subversion) the changed files in the 
following two directories:

- `content/post`
- `docs`

and you are done. 

### 4. Step) Visit the updated blog

The content of the updated blog is available at [http://kwb-r.github.io/fakin.blog](http://kwb-r.github.io/fakin.blog).
