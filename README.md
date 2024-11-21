The following is paraphrased from
https://jupyterbook.org/en/stable/start/publish.html

To make changes to wedding website:

1. Make changes to local md files in ~/MAS2004,9/MAS2004,9Sem2Notes

2. Rebuild jupyter book with 
cd ~/Wedding
jupyter-book build MAS2004,9Sem2Notes/

3. Sync with main branch of this repository

4. Use 
cd MAS2004,9Sem2Notes
ghp-import -n -p -f _build/html
to push the newly built HTML to the gh-pages branch of this repository.

This will require signing in
Username: RosieSB
Password: Go to https://github.com/settings/tokens to generate a personal access key
