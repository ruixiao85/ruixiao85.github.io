# Set up and try the example site
```ps1
conda install -c conda-forge nodejs
npm install postcss-cli

mkdir themes
cd themes

# git clone https://github.com/apvarun/blist-hugo-theme.git blist
# cd blist/exampleSite/
# hugo serve --themesDir ../..

git clone https://github.com/LucasVadilho/heyo-hugo-theme
cd heyo-hugo-theme/exampleSite
hugo server --themesDir ../..

```

# Start with example site

```ps1
# back to project root directory
Copy-Item -Path themes/heyo-hugo-theme/exampleSite/* -Destination . -Recurse
hugo

```