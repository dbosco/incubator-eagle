<!--
{% comment %}
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to you under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
{% endcomment %}
-->

# Eagle Documentation

Eagle documentation repository for content available on http://eagle.incubator.apache.org/docs/

Documentation is written in [Markdown](https://guides.github.com/features/mastering-markdown/) format and statically generated into HTML using [MkDocs](http://www.mkdocs.org/).  All documentation is located in the [eagle-docs](.) directory, and [mkdocs.yml](../mkdocs.yml) file describes the navigation structure of the published documentation.

## Requirements
* Python 2.x: https://www.python.org/
* MkDoc: http://www.mkdocs.org/

## Installation
1. Validate versions of Python (tested under `python 2.7`) and python package management tool
    
        $ python --version

        # At least one of follow python package management tools should be installed
        $ easy_install --version
        $ pip --version

  > __NOTES__
  >
  > MkDocs is built upon Python, before starting to install MkDocs, please make sure you verify at least one python package management tool like `easy_install` or `pip` has been installed
  >- How to install easy_install? https://pypi.python.org/pypi/setuptools#installation-instructions
  >- How to install pipe? https://pip.readthedocs.org/en/stable/installing/#install-pip
  
2. Install `MkDocs`: [http://www.mkdocs.org/#installation](http://www.mkdocs.org/#installation)
  
        sudo easy_install install mkdocs
  
  or 
  
      sudo pip install mkdocs

## Reading

Execute `mkdocs serve` under project base where [`mkdocs.yml`](../mkdocs.yml) is and open [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to start reading.

    cd incubator-eagle
    mkdocs serve

## Authoring

New pages can be added under [eagle-docs](.) or related sub-category, and a reference to the new page must be added to the [mkdocs.yml](../mkdocs.yml#L36) file to make it availabe in the navigation.  Embedded images are typically added to images folder at the same level as the new page.

When creating or editing pages, it can be useful to see the live results, and how the documents will appear when published.  Live preview feature is available by running the following command at the root of the repository:

```bash
mkdocs serve
```

For additional details see [writing your docs](http://www.mkdocs.org/user-guide/writing-your-docs/) guide.

## Site Configuration

Guides on applying site-wide [configuration](http://www.mkdocs.org/user-guide/configuration/) and [themeing](http://www.mkdocs.org/user-guide/styling-your-docs/) are available on the MkDocs site.

## Deployment

Deployment is done in two steps.  First all documentation is statically generatd into HTML files and then it is deployed to the eagle website.  For more details on how conversion to HTML works see [MkDocs documentation](http://www.mkdocs.org/).


1.  Go to release branch of the repository and execute the following command to build the docs.  

    > **Note**: Until [mkdocs #859](https://github.com/mkdocs/mkdocs/issues/859) is resolved and available for download, use mkdocs built against [master](https://github.com/mkdocs/mkdocs).
    
    ```bash
    # set project version
    EAGLE_VERSION=0.3.0
    
    # build docs under site foolder
    mkdocs build --clean
    
    # copy docs from site into target folder on eagle-site
    cd ../incubator-eagle-svn
    cp -r ../incubator-eagle/site site/docs/${EAGLE_VERSION}
    # Set this to be latest available docs version
    git add -A
    git commit -m "Adding eagle-${EAGLE_VERSION} documentation"
    git push
    ```

2. Add link to landing site

    > `TODO`
