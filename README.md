# agents2.app
Personal AI and cloud portfolio site for Baba Shaik, Principal Cloud Architect.
## Structure
- `index.html` - homepage, loads and renders `projects.json`
- - `styles.css` - site styling
  - - `projects.json` - list of projects (name, description, tech tags, screenshot path, GitHub link, status). Edit this file and push to add or update a project; the homepage renders from it automatically.
    - - `assets/screenshots/` - project screenshots referenced by `projects.json`
      - - `CNAME` - required by GitHub Pages for the custom domain
        - ## Project status values
        - - `Active` - currently in progress, shown first
          - - `Prototype` - working experiment, documented rather than run live
            - - `Archived` - earlier project, shown in the archive list
              - ## Hosting setup
              - **1. GitHub Pages**
              - This repo must be named `BfShaik.github.io` and pushed to the `main` branch. In the repo Settings -> Pages:
              - - Source: deploy from `main` branch, root
                - - Custom domain: `agents2.app`
                  - - Wait for the DNS check to pass, then enable Enforce HTTPS
                    - **2. DNS at Namecheap**
                    - Domain List -> Manage `agents2.app` -> Advanced DNS. Add four A records for host @ pointing to 185.199.108.153, 185.199.109.153, 185.199.110.153, and 185.199.111.153, plus a CNAME record for host www pointing to BfShaik.github.io.
                    - Propagation can take anywhere from a few minutes to a few hours.
                    - ## Adding a new project
                    - 1. Add a new object to `projects.json` with the project's details.
                      2. 2. Drop a screenshot into `assets/screenshots/` matching the path referenced in the entry.
                         3. 3. Commit and push. GitHub Pages rebuilds automatically.
                            4. ## Adding screenshots
                            5. The homepage will show "Screenshot coming soon" for any project whose screenshot file is not yet present, so it is safe to add project entries before the image exists.
                            6. 
