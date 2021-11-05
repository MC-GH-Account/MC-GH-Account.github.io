---
title: Projects
altLangPage: /fr/projets
dateModified: 2021-11-04
description: "Partner with us"
lang: en
---

## Projects

<!---

Edit this section to change the description for the projects page.
This is not the place to add new projects, those should be done in the location:
    /_data/components.json

For more information about editting the json file read:
    https://www.w3schools.com/js/js_json_intro.asp

--->
Nam accumsan feugiat sapien ut lacinia. Suspendisse dignissim pharetra est id rutrum. Nam sed congue est, vel hendrerit tellus. Curabitur vestibulum porta accumsan. Sed vulputate pretium neque, congue facilisis lacus fringilla nec. Morbi id magna accumsan, semper nibh ac, imperdiet turpis.

Duis vitae nisl quis justo dignissim bibendum eget eu tellus. Curabitur iaculis, sapien sit amet ullamcorper ullamcorper, tellus sem efficitur leo, ac hendrerit velit nisi at eros. Nullam laoreet suscipit justo vel scelerisque. Aenean sit amet maximus odio, ac semper augue. Mauris scelerisque consectetur consequat. Nam vestibulum elit sed urna lacinia tempor. Donec tincidunt libero tellus. Morbi consequat tempus risus, a pharetra lacus efficitur sit amet. Nam eu rhoncus magna. Pellentesque nec elit placerat sem egestas vestibulum vel vitae ipsum. Donec tempor, urna sit amet semper rhoncus, augue ex tristique enim, eu vestibulum urna risus non turpis. Maecenas at nibh hendrerit, feugiat ante sit amet, volutpat dolor. Pellentesque sollicitudin ex id massa pulvinar, nec pharetra quam blandit.

<!---

Edit this section to change way that the component boxes are rendered.
Components are read from the following location:
    /_data/components.json

For more information about editting the json file read:
    https://www.w3schools.com/js/js_json_intro.asp

For more info about how this is rendered:
    https://www.w3schools.com/bootstrap4/

--->
{::nomarkdown}
{% assign page_group = site.data.i18n.page_group[ page.lang ] %}

<div class="container">
  <div class="row">
    <!--- For each project in data-project --->
    {% assign components = site.data.components %}
    {% for component in components %}
    <div class="col-6 my-3">
      <div class="mx-2 p-3 cell">
        <!--- currentProject.Title--->
        <div class="cell-title">
          <h3>{{ component.title[ page.lang ] }}</h3>
        </div>
        <!--- currentProject.Description--->
        <div class="cell-description">
          <p>{{ component.description[ page.lang ] }}</p>
        </div>
        <div class="container">
          <!--- For each link in currentProject.links --->
          {% for pgGroup in component.pages %}
            {% assign grpkey = pgGroup[0] %}
            <div class="row cell-url">
                <div class="col-2">
                {{ page_group[ grpkey ] | default: "View" }}: 
                </div>
                {% assign examples = pgGroup[1] | where: "language", page.lang %}
                {% for example in examples %}
                    {% if example.path %}
                        <div class="col">
                        <a href="{{  example.path  }}">{{ example.title }}</a>
                    {% elsif example.url %}
                        <div class="col">
                        <a href="{{  example.url  }}">{{ example.title }}</a>
                    {% else %}
                        <li>{{ example.title }}</li>
                    {% endif %}
                {% endfor %}
                </div>
            </div>
          {% endfor %}
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
</div>  
</br></br>
{:/}

[Back](./)
