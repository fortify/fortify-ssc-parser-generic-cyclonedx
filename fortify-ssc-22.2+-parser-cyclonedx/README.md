<x-tag-head>
<x-tag-meta http-equiv="X-UA-Compatible" content="IE=edge"/>

<x-tag-script language="JavaScript"><!--
<X-INCLUDE url="https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@10.0.0/build/highlight.min.js"/>
--></x-tag-script>

<x-tag-script language="JavaScript"><!--
<X-INCLUDE url="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js" />
--></x-tag-script>

<x-tag-script language="JavaScript"><!--
<X-INCLUDE url="${gradleHelpersLocation}/spa_readme.js" />
--></x-tag-script>

<x-tag-style><!--
<X-INCLUDE url="https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@10.0.0/build/styles/github.min.css" />
--></x-tag-style>

<x-tag-style><!--
<X-INCLUDE url="${gradleHelpersLocation}/spa_readme.css" />
--></x-tag-style>
</x-tag-head>

# Fortify SSC 22.2+ Parser Plugin for CycloneDX

## Introduction

This Fortify SSC parser plugin allows for importing [CycloneDX](https://cyclonedx.org/) SBOM files into SSC. This version of the plugin can be used on Fortify SSC version 22.2 and above, and allows for displaying CycloneDX results on SSC's Open Source page.

### Limitations

* **Actual results may vary depending on input**  
  For example, due to the flexibility of the CycloneDX specification:  
    * Some CycloneDX input files may not include vulnerability data, which may result in failing or empty import
    * The plugin may be unable to calculate consistent, unique issue instance id's because the input file doesn't provide sufficient details to uniquely identify an issue
    * The plugin may not be able to determine Fortify Priority Order because the input file does not provide issue severity levels
    * The plugin may be unable to display appropriate issue category or description because the input file is lacking this information, or providing this information in a non-standard way 

* **CycloneDX results from multiple tools cannot be uploaded to single SSC application version**  
  Being a generic format, you may have multiple tools generating CycloneDX files that you want to import into SSC. Due to limitations in the SSC parser framework, it is currently not possible to import CycloneDX files from different sources into a single SSC application version. Independent of which tool was actually used to generate the CycloneDX file, SSC will assume that all CycloneDX files originate from the same scan engine. SSC will try to merge these uploads, thereby basically marking all issues from a previously uploaded CycloneDX file as 'removed'.

### Related Links

* **Downloads**: https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx/releases
    * _Development releases may be unstable or non-functional. The `thirdparty.zip` file is for informational purposes only and does not need to be downloaded._
* **Sample input files**: [sampleData](sampleData)
* **GitHub**: https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx
* **Automated builds**: https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx/actions
* **CycloneDX website**: https://cyclonedx.org/

## Plugin Installation

These sections describe how to install, upgrade and uninstall the plugin.

### Install & Upgrade

* Obtain the plugin binary jar file
	* Either download from GitHub Releases page (see [Related Links](#related-links)) 
	* Or by building yourself (see [Developers](https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx#developers))
* If you already have another version of the plugin installed, first uninstall the previously installed version of the plugin by following the steps under [Uninstall](#uninstall) below
* In Fortify Software Security Center:
	* Navigate to Administration->Plugins->Parsers
	* Click the `NEW` button
	* Accept the warning
	* Upload the plugin jar file
	* Enable the plugin by clicking the `ENABLE` button
  
### Uninstall

* In Fortify Software Security Center:
	* Navigate to Administration->Plugins->Parsers
	* Select the parser plugin that you want to uninstall
	* Click the `DISABLE` button
	* Click the `REMOVE` button 

## Obtain results

You will need to download results in CycloneDX format from your preferred product, after which these results can be uploaded to Fortify SSC. SSC parser plugins cannot retrieve results from 3<sup>rd</sup>-party systems directly.

## Upload results

As a 3<sup>rd</sup>-party results zip bundle:

* Generate a scan.info file containing a single line as follows:  
          `engineType=CYCLONEDX`
* Generate a zip file containing the following:
	* The scan.info file generated in the previous step
	* The JSON file containing scan results
* Upload the zip file generated in the previous step to SSC
	* Using any SSC client, for example FortifyClient or Maven plugin
	* Or using the SSC web interface
	* Similar to how you would upload an FPR file

## License
<x-insert text="<!--"/>

See [LICENSE.TXT](../LICENSE.TXT)

<x-insert text="-->"/>

<x-include url="file:LICENSE.TXT"/>

