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

# Fortify SSC Parser Plugin for Debricked

## Introduction

This Fortify SSC parser plugin allows for importing [Debricked](https://debricked.com/) files in [CycloneDX](https://cyclonedx.org/) SBOM format into SSC. This plugin has been tested with SSC 22.1, but should be compatible with all recent SSC versions. Although this version of the plugin should function fine on SSC 22.2 and above, please note that there is a dedicated SSC 22.2+ version of the plugin that allows for displaying CycloneDX results on SSC's Open Source page.

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

You will need to download results in CycloneDX format from Debricked, after which these results can be uploaded to Fortify SSC. SSC parser plugins cannot retrieve results from 3<sup>rd</sup>-party systems directly.

## Upload results

As a 3<sup>rd</sup>-party results zip bundle:

* Generate a scan.info file containing a single line as follows:  
          `engineType=DEBRICKED`
* Generate a zip file containing the following:
	* The scan.info file generated in the previous step
	* The JSON file containing scan results
* Upload the zip file generated in the previous step to SSC
	* Using any SSC client, for example FortifyClient or Maven plugin
	* Or using the SSC web interface
	* Similar to how you would upload an FPR file

As raw scan results:  

* Navigate to the Artifacts tab of your application version
* Click the `UPLOAD` button
* Click the `ADD FILES` button, and select the JSON file to upload
* Enable the `3rd party results` check box
* Select the `DEBRICKED` type

*Note that uploading raw scan results is only supported for manual uploads through the SSC web interface, and this functionality was removed in SSC 20.2 so no longer available in recent SSC versions. Please submit a feature request if you'd like to see this easier process for ad-hoc uploading of 3<sup>rd</sup>-party results restored, referencing Octane id #448174.*

## License
<x-insert text="<!--"/>

See [LICENSE.TXT](../LICENSE.TXT)

<x-insert text="-->"/>

<x-include url="file:LICENSE.TXT"/>

