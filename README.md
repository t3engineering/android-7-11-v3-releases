# ios-7-11-v3-releases
This repo is used to generate [GitHub pages](https://pages.github.com), which displays [our v3.x releases](https://t3engineering.github.io/ios-7-11-v3-releases/) for the 7-11 iOS project, which you can find [here](https://t3engineering.github.io/ios-7-11-v3-releases/).

I'm currently working on automating our release process, but at the moment it's completely manual. To release a new build:

1. Merge your new changes into the `qa` branch on the [iOS 3.0 repository in GitLab](https://gitlab.t-3.com/7-eleven/7-11-sherman-ios-3-0/).

2. Download the IPA from the build machine in GitLab, [here](https://gitlab.t-3.com/7-eleven/7-11-sherman-ios-3-0/builds). To get there manually, go to: Repository ➡️ Pipelines ➡️ Builds ➡️ and click the download button of the archive you would like. Archives should only be generated on the `qa` branch. 

  ![Where to download builds.](img/download-button.png "Where to download builds.")
	

3. Update plist to contain the new `.ipa` name and new version number.
	
	![](img/plist.png)

	> Pre v1.0 version numbers are `0.sprint-number.build-number-in-sprint`. So the 4th build in sprint #6 would be `0.6.4`.

4. Add an additional entry to the top of `index.html` with the new version, including a link to the release notes in the form of `1.04-Release-Notes.html`, for example.

5. To generate the release notes, we use JIRA. Go to [our project page](https://jira.t-3.com/secure/RapidBoard.jspa?rapidView=10006&projectKey=SVELIOSTWO) and select all of the tasks in the "Dev Completed" column. Then:
	1. Right click your selection, and select `Bulk change`.
	2. Select `Edit issues` and continue.
	3. Tick `Change Affects Version/s`, and type in your new version.
	4. Now click Releases in the sidebar.
	5. Select your new version.
	6. Get the auto generated release notes from JIRA near the top of the page.
	![](img/release-notes.png)
	7. Paste them into your new `Release-Notes.html` file.
6. Push your changes! They should now be publically visible at [t3engineering.github.io/ios-7-11-v3-releases](https://t3engineering.github.io/ios-7-11-v3-releases/).

# Known Issues
GitHub would prefer us to use their Releases product to send out binaries. When we push an update, GitHub sends a warning email, which is summed as:

> It looks like you're using GitHub Pages to distribute binary files. We strongly suggest that you use releases to ship projects on GitHub. Releases are GitHub's way of packaging and providing software to your users. 

I don't think Releases is the right solution for us because we are often delivering builds to non-technical users. If anyone has an idea to fix this, (besides a filter for that email 😛) that would be great.
