For some specific use cases, you might want to use your own fork. For example, if you wish to make your own additions that are not included in the main repository, or if you need to use your own build environment due to different hardware, we have developed a way to still use OTA updates in such cases. This is achieved by enabling the ability to switch the repository used for updates.

To configure this, first, create your own fork. Make changes to your liking, such as adding or removing build environments in the `platformio.ini` file. You may want to take precautions to ensure that your changes will not be overwritten if you synchronize your fork with the upstream repository. How to do this is beyond the scope of this documentation.

Secondly, modify the build scripts to include the correct build environments. Edit `/.github/workflows/release.yml` and add or remove the `Build firmware for ...` sections to generate the precompiled binaries in a release. You might also want to edit `/.github/workflows/build-test.yml` to achieve the same for the build tests. Ensure that these modifications are not overwritten if these files change in the upstream repository.

Now, create a release in your GitHub repository. The releases will be used for the OTA updates. The release script (which will run automatically when you add a release) will include the necessary files (some .json files and the precompiled binaries) in the release. This process takes approximately 10 minutes to complete (observe the 'actions' tab on GitHub to monitor its progress).

On the OpenEpaperLink webpage, navigate to the config page and locate the update button. Here, you can select the repository to be used for OTA updates. Fill in the form as `username/reponame`, click 'change,' select the build environment, and then click 'confirm.' From this point forward, any OTA updates will be performed using the releases you created in your fork. This allows other users to effortlessly switch repositories without having to compile the project themselves.

![ota-repo](https://github.com/jjwbruijn/OpenEPaperLink/assets/4137036/25de58f9-5393-4eb5-ba1d-2cb4430afadc)
