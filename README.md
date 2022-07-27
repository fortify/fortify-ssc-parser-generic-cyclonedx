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

# Fortify SSC Parser Plugins for CycloneDX & Debricked

## Introduction

This repository provides the following plugins:

* [CycloneDX plugin](fortify-ssc-parser-cyclonedx)
    * Fortify SSC parser plugin for importing generic [CycloneDX](https://cyclonedx.org/) SBOM files containing open source vulnerability data
	* Compatible with all recent SSC versions
	* CycloneDX vulnerability data shown on SSC Audit page only
* [CycloneDX plugin for SSC 22.2+](fortify-ssc-22.2+-parser-cyclonedx)
    * Fortify SSC parser plugin for importing generic [CycloneDX](https://cyclonedx.org/) SBOM files containing open source vulnerability data
	* Compatible with SSC 22.2 and above
	* CycloneDX vulnerability data shown on SSC's Open Source page
* [Debricked plugin](fortify-ssc-parser-debricked)
    * Fortify SSC parser plugin for importing [Debricked](https://debricked.com/) results in [CycloneDX](https://cyclonedx.org/) SBOM format containing open source vulnerability data
	* Compatible with all recent SSC versions
	* Debricked vulnerability data shown on SSC Audit page only
* [Debricked plugin for SSC 22.2+](fortify-ssc-22.2+-parser-debricked)
    * Fortify SSC parser plugin for importing [Debricked](https://debricked.com/) results in [CycloneDX](https://cyclonedx.org/) SBOM format containing open source vulnerability data
	* Compatible with SSC 22.2 and above
	* Debricked vulnerability data shown on SSC's Open Source page

Please refer to the links above for usage instructions for each of these plugins.

### Related Links

* **Downloads**: https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx/releases
    * _Development releases may be unstable or non-functional. The `thirdparty.zip` file is for informational purposes only and does not need to be downloaded._
* **Sample input files**: [sampleData](sampleData)
* **GitHub**: https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx
* **Automated builds**: https://github.com/fortify-ps/fortify-ssc-parser-cyclonedx/actions
* **CycloneDX website**: https://cyclonedx.org/
* **Debricked website**: https://debricked.com/

## Developers

The following sections provide information that may be useful for developers of these parser plugins.

### IDE's

This project uses Lombok. In order to have your IDE compile this project without errors, 
you may need to add Lombok support to your IDE. Please see https://projectlombok.org/setup/overview 
for more information.

### Gradle Wrapper

It is strongly recommended to build this project using the included Gradle Wrapper
scripts; using other Gradle versions may result in build errors and other issues.

The Gradle build uses various helper scripts from https://github.com/fortify-ps/gradle-helpers;
please refer to the documentation and comments in included scripts for more information. 

### Common Commands

All commands listed below use Linux/bash notation; adjust accordingly if you
are running on a different platform. All commands are to be executed from
the main project directory.

* `./gradlew tasks --all`: List all available tasks
* Build: (plugin binaries will be stored in `build/libs`)
	* `./gradlew clean build`: Clean and build the project
	* `./gradlew build`: Build the project without cleaning
	* `./gradlew dist distThirdParty`: Build distribution zip and third-party information bundle
* `./fortify-scan.sh`: Run a Fortify scan; requires Fortify SCA to be installed

### Automated Builds

This project uses GitHub Actions workflows to perform automated builds for both development and production releases. All pushes to the main branch qualify for building a production release. Commits on the main branch should use [Conventional Commit Messages](https://www.conventionalcommits.org/en/v1.0.0/); it is recommended to also use conventional commit messages on any other branches.

User-facing commits (features or fixes) on the main branch will trigger the [release-please-action](https://github.com/google-github-actions/release-please-action) to automatically create a pull request for publishing a release version. This pull request contains an automatically generated CHANGELOG.md together with a version.txt based on the conventional commit messages on the main branch. Merging such a pull request will automatically publish the production binaries and Docker images to the locations described in the [Related Links](#related-links) section.

Every push to a branch in the GitHub repository will also automatically trigger a development release to be built. By default, development releases are only published as build job artifacts. However, if a tag named `dev_<branch-name>` exists, then development releases are also published to the locations described in the [Related Links](#related-links) section. The `dev_<branch-name>` tag will be automatically updated to the commit that triggered the build.


## License
<x-insert text="<!--"/>

See [LICENSE.TXT](LICENSE.TXT)

<x-insert text="-->"/>

<x-include url="file:LICENSE.TXT"/>

