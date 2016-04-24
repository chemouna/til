

### Configure lint to exclude verification of an issue on some files

Sometimes lint reports an issue that either because its in a library i cant fix or 
i just explicitly dont want lint to report it we can create a lint.xml file in project folder
and specify the issue and what we want to do, like in the example below where 
i want to exclude an issue in butterknife from being reported untill it is fixed in butterknife.


```xml
<?xml version="1.0" encoding="UTF-8"?>
<lint>

  <issue id="ResourceType">
    <!-- Remove this when this is fixed: https://github.com/JakeWharton/butterknife/issues/338 -->
    <ignore path="**/*$$ViewBinder.java" />
  </issue>

</lint>

```
