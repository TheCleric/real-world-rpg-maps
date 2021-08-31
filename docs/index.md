<script>
    function generateMap() {
        mapImg = document.getElementById("map-img");
        radius = document.getElementById("radius").value;

        var request = new XMLHttpRequest();

        var onRequestLoad = function() {
            if (this.status == 200) {
                result = JSON.parse(this.responseText);
                mapImg.src = 'data:image/svg+xml;base64,' + result.map;
            } else {
                alert('Error: ' + this.status);
                mapImg.src = '';
            }
        };

        mapImg.src = 'spinner.gif';

        var url = 'https://real-world-rpg-maps-staging.herokuapp.com/';
        if (radius !== '') {
            url += '?radius=' + radius;
        }

        request.addEventListener('load', onRequestLoad);
        request.open('GET', url);
        request.send();
    }
</script>

<div>
    <div>
        <input type="number" id="radius" placeholder="Radius" />
    </div>
    <div>
        <button onclick="generateMap()">Generate Map!</button>
    </div>
    <div>
        <img id="map-img"/>
    </div>
</div>

<!--
## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/TheCleric/real-world-rpg-maps/edit/main/docs/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/TheCleric/real-world-rpg-maps/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
-->