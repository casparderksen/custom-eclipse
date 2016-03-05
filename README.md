# Branded Eclipse Example

Build an own, branded eclipse with a couple of plugins already installed an selected.

## Download

Prepackaged eclipse archives can be downloaded here:

<https://sourceforge.net/projects/custom-eclipse/files/>


## How-To create eclipse yourself

1.  Make sure, you have the necessary utilities installed: `apt-get install zip unzip tar sed java svn wget git bash`.
2.  Clone this repository: `git clone https://github.com/adangel/custom-eclipse`
3.  Review `create-mirror.sh` and comment/uncomment the update sites you want to mirror
4.  Execute `bash create-mirror.sh`
5.  Drink coffee. This can take a while. If every update site is enabled, you'll download about 5 gigabytes.
    All the downloaded stuff will be placed under `temp/`. Under `temp/p2-mirror` is a merged p2 repository
    which contains all the artifacts of the mirrored repositories.
6.  Have a look at the module "branding". This is a eclipse plugin which brings
    *   A splash screen. Replace "splash-base.bmp" with your own.
    *   The project uses "splasher-maven-plugin". Update the property `splash-subtitle` in the top-level pom.xml file.
    *   Icons. Replace icon*.* with your own.
    *   About dialog in eclipse. See plugin.xml/plugin.properties for details. See also about.gif for the logo
        in the about dialog.
7.  Have a look at "feature/feature.xml". This selects hopefully all the features, that come with the default
    Eclipse JEE bundle. You can add/remove features and plugins.
8.  Have a look at "feature-plugins/feature.xml". This selects all additional features/plugins from external sites
    that have been mirrored.
9.  Have a look at the top-level pom.xml file. You can specify for which platforms you want to create an
    own eclipse distribution. See the plugin "target-platform-configuration" and the environments configuration.
10. Execute `mvn clean package`. The result is stored under "distribution/target/products/".
11. Last step: Execute `fix-javagent-paths.sh`. This will change the absolute paths to the java agents
    in "eclipse.ini" to relative ones and repackage the eclipse archives.
12. The final result is still stored under "distribution/target/products/".



## Starting Eclipse

The created eclipse distribution contains two javaagents: lombok and optimizer-for-eclipse.
If eclipse doesn't start, you maybe need to adjust the paths in `eclipse.ini`.

## Plugins

List of the contained plugins with update sites in no specific order.

* [ResourceBundle Editor](http://eclipse-rbe.sourceforge.net/) - <http://sourceforge.net/projects/eclipse-rbe/files/Eclipse%203.x/0.8.0/ResourceBundleEditor_v0.8.0.zip> (no update site)
* [JUtils ToString Generator](http://eclipse-jutils.sourceforge.net/) <http://sourceforge.net/projects/eclipse-jutils/files/eclipse-jutils/eclipse-jutils%20plugin%20v3.1/org.adarsh.jutils_3.1.0.zip> (no update site)
* [Checkstyle](http://eclipse-cs.sourceforge.net/) - <http://eclipse-cs.sourceforge.net/update/>
* [Spring Tool Suite](http://www.springsource.org/sts) - <http://dist.springsource.com/release/TOOLS/update/e4.2>
* [Maven Integration (m2e)](http://eclipse.org/m2e/) - <http://download.eclipse.org/technology/m2e/releases>
* [Findbugs](http://findbugs.sourceforge.net/) - <http://findbugs.cs.umd.edu/eclipse/>
* [EclEmma](http://www.eclemma.org/) - <http://update.eclemma.org/>
* [PMD](http://pmd.sourceforge.net) - <http://pmd.sourceforge.net/eclipse/>
* [EGit](http://www.eclipse.org/egit/) - <http://download.eclipse.org/egit/updates>
* [Jenkins](https://code.google.com/p/jenkins-eclipse-plugin/) - <http://jenkins-eclipse-plugin.googlecode.com/svn/trunk/jenkins-update/>
* [Aptana Studio 3](http://www.aptana.com/products/studio3) - <http://download.aptana.com/studio3/plugin/install>
* [JAutodoc](http://jautodoc.sourceforge.net/) - <http://jautodoc.sourceforge.net/update/>
* [ExploreFS](http://www.junginger.biz/eclipse/index.html) - <http://www.junginger.biz/eclipse/>
* [Atlassian Clover](http://www.atlassian.com/software/clover/) - <http://update.atlassian.com/eclipse/clover/>
* [Json Editor](https://sourceforge.net/projects/eclipsejsonedit/) - <http://sourceforge.net/projects/eclipsejsonedit/files/eclipsejsonedit/Json%20Editor%20Plugin%200.9.4/JsonEditorPlugin-0.9.4.zip> (no update site)
* [JadClipse](http://jadclipse.sourceforge.net) - <http://jadclipse.sourceforge.net/update/>
* [Lint4j](http://www.jutils.com/) - <http://www.jutils.com/eclipse-update/>
* [JDepend4Eclipse](http://andrei.gmxhome.de/jdepend4eclipse/) - <http://andrei.gmxhome.de/eclipse/>
* [JBoss Tools](http://www.jboss.org/tools) - <http://download.jboss.org/jbosstools/updates/stable/juno/>
* [m2e-code-quality](http://m2e-code-quality.github.io/m2e-code-quality/) - <http://m2e-code-quality.github.io/m2e-code-quality/site/1.0.0>
* [m2e-wtp](http://www.eclipse.org/m2e-wtp/) - <http://download.eclipse.org/m2e-wtp/releases/>
* [Atlassian IDE Connectors](http://www.atlassian.com/software/ide-connectors/) - <http://update.atlassian.com/atlassian-eclipse-plugin/rest/e3.6/>
* [EasyShell](http://pluginbox.sourceforge.net/plugins.html) - <http://pluginbox.sourceforge.net/>
* [m2e-jaxb](http://bitstrings.github.io/) - <http://bitstrings.github.io/m2e-connectors-p2/releases/>
* [m2e-antrun](http://code.google.com/p/nl-mwensveen-m2e-extras/) - <http://nl-mwensveen-m2e-extras.googlecode.com/svn/trunk/p2>
* [TestNG](http://testng.org/doc/eclipse.html) - <http://beust.com/eclipse>
* [Doxia IDE](http://maven.apache.org/doxia/doxia-ide/eclipse/) - <http://maven.apache.org/doxia/doxia-ide/eclipse/eclipse/>
* [Markdown Editor](http://www.winterwell.com/software/markdown-editor.php) - <http://www.winterwell.com/software/updatesite/>
* [JSLint integration for the Eclipse IDE](https://github.com/weightpoint/jslint-eclipse) - <http://weightpoint.github.io/jslint-eclipse/updates/>
* [APT-Connector for M2E](https://code.google.com/p/apt-m2e/) - <http://apt-m2e.googlecode.com/git/updateSite/>
* [Optimizer for Eclipse](http://zeroturnaround.com/free/optimizer-for-eclipse/) - <http://update.zeroturnaround.com/free-tools/site/>
* [Eclipse Subversive - Subversion (SVN) Team Provider](http://eclipse.org/subversive/) - <http://download.eclipse.org/technology/subversive/2.0/update-site/>

## References

* [Eclipse Magazin](http://www.eclipse-magazin.de), Issue 5.12, Page 52
* <http://wiki.eclipse.org/Tycho/Demo_Projects/RCP_Application>
* <https://github.com/rombert/scripts/blob/master/bin/mirror_eclipse_update_site.sh>
* <http://wiki.eclipse.org/Equinox_p2_Repository_Mirroring>
* <http://stackoverflow.com/questions/1371176/downloading-eclipse-plug-in-update-sites-for-offline-installation>
* <http://wiki.eclipse.org/Equinox/p2/Publisher#Features_And_Bundles_Publisher_Application>
* <http://wiki.eclipse.org/Tycho/Packaging_Types>
* <http://eclipse.org/tycho/sitedocs/tycho-p2/tycho-p2-director-plugin/archive-products-mojo.html>
* <http://stackoverflow.com/questions/8583878/rename-zip-files-created-by-tycho-p2-director-plugin>
* <http://wiki.eclipse.org/Simultaneous_Release>
* <http://wiki.eclipse.org/Eclipse_Project_Update_Sites>


