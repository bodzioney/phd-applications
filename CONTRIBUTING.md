# Contributing

Thanks for helping keep this directory up to date!

## How it works

The entries for schools and professors go in **`_data/directory.yml`**. Both the
README and the
[GitHub Pages site](https://bodzioney.github.io/phd-applications/) are generated
from this file.

**Do not edit `README.md` directly** — your changes will be overwritten the next
time the README is regenerated. However, I will not stop you. One must imagine
Sisyphus happy.

## Adding or updating a professor

Edit `_data/directory.yml`. Each professor entry looks like this:

```yaml
- name: Jane Smith
  homepage: https://example.com/~jsmith
  scholar: https://scholar.google.com/citations?user=XXXXXXXXXXXX
  orcid: https://orcid.org/0000-0000-0000-0000
  dblp: https://dblp.org/pid/XX/XXXX.html
  research: type systems, formal methods, program verification
  taking_students: true    # true, false, or omit if unknown
  image: /assets/img/profiles/jane-smith.jpg  # optional
```

All fields except `name` are optional.

### Adding a new university

Add a new entry under the appropriate country:

```yaml
- name: University Name
  url: https://department-url.example.com   # optional
  deadline: December 15th                    # or omit if unknown
  deadline_url: https://admissions-link.com  # optional
  professors:
    - name: ...
```

For universities with multiple deadlines, use a list:

```yaml
  deadline:
    - "Fall: December 15th"
    - "Spring: June 1st"
```

If a deadline item has its own URL (like Lisboa's program-specific links):

```yaml
  deadline:
    - text: "CMU Portugal Affiliated PhD: May 12th"
      url: https://cmuportugal.org/affiliated-ph-d-programs/
```

If it is more complicated than this, please link the arXiv paper explaining the
admissions process for that specific university.

## Adding a profile picture

The site is configured to use the linked Google Scholar profile picture by
default.

If the Google Scholar picture is not flattering enough, you can override it by
adding an image to `assets/img/profiles/` (use `firstname-lastname.jpg`) and
adding an `image` field to the professor's YAML entry:

```yaml
  image: /assets/img/profiles/firstname-lastname.jpg
```

If there is no image field or Google Scholar, we default to a letter
placeholder[^1].

## Regenerating the README

First, install python dependencies:

```
# Create a virtual environment (optional but recommended)
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

After editing the YAML, you can manually regenerate the README:

```
python scripts/generate_readme.py
```

Or just push and let the workflow do it.

## Previewing the site locally

```
jekyll --run "jekyll serve --port 4000"
```

Then open http://localhost:4000/phd-applications/.

[^1]: Visualizing this professor is left as an exercise to the reader.
