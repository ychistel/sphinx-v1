Ceci est une page de test 2
===========================

Premier workflow
----------------

Le code du fichier sphinx.yml

On fait une petite modif pour voir si ça commit bien ! Encore un peu plus.

Le dépôt est maintenant privé ! Mais ça ne marche pas...

On protège la branche master

.. code-block:: yaml
   
   name: Sphinx Documentation

   on:
      push:
         branches:
            - main

   jobs:
   deploy:
      runs-on: ubuntu-latest

      steps:
      - name: Checkout repository
            uses: actions/checkout@v2

      - name: Set up Python
            uses: actions/setup-python@v2
            with:
            python-version: 3.x

      - name: Install dependencies
            run: |
            python -m pip install --upgrade pip
            pip install -r requirements.txt

      - name: Build documentation
            run: |
            sphinx-build -b html source build

      - name: Deploy to GitHub Pages
            uses: peaceiris/actions-gh-pages@v3
            if: github.ref == 'refs/heads/main'
            with:
            github_token: ${{ secrets.GITHUB_TOKEN }}
            publish_branch: github-pages
            publish_dir: ./build

Voila fin du fichier yaml.

Toujours pas de mise à jour !!


