1. Create virtual environment (do once)

python3 -m venv .venv

2. Activate it (do every time)

source .venv/bin/activate

3. Install any packages needed for this project. e.g.

pip3 install jupyter-book

or

python3 -m pip install jupyter-book

4. To make changes to notes:
- Make changes to local files in ~/my_project_dir/MAS2004-9Sem2Notes
- Rebuild jupyter book with 
cd ~/MAS2004,9/MAS2004\ Jupyter\ notes
jupyter-book build MAS2004-9Sem2Notes/


-----------------------------------
FOR LATER IF USING GITHUB PAGES

The following is paraphrased from
https://jupyterbook.org/en/stable/start/publish.html

To make changes to notes:

1. Make changes to local files in ~/my_project_dir/MAS2004-9Sem2Notes

2. Rebuild jupyter book with 
cd ~/my_project_dir
jupyter-book build MAS2004-9Sem2Notes/

3. Sync with main branch of this repository

4. Use 
cd MAS2004-9Sem2Notes
ghp-import -n -p -f _build/html
to push the newly built HTML to the gh-pages branch of this repository.

This will require signing in
Username: RosieSB
Password: Go to https://github.com/settings/tokens to generate a personal access key
