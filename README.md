![Bitrocket Logo][bitrocketlogo]
<br />
# Bitrocket
<br />
<p>
<b><a href="#overview">Overview</a></b>
|
<b><a href="#features">Features</a></b>
|
<b><a href="#installation">Installation</a></b>
|
<b><a href="#team">Team</a></b>
|
<b><a href="#license">Copyright & License</a></b>
</p>
<br /><br />

## Overview <a name="overview"></a>
Connect [Alassian BitBucket Server][BitBucketserver] or [Alassian BitBucket Cloud][BitBucketcloud] with [Rocket.Chat][rocketchat] and send notifications to users or channels on each push, pull requests or comments on pull requests to any branch.
<br /><br /><br /><br />

## Features <a name="features"></a>
This script uses BitBuckets Post-Receive WebHooks to submit a payload to your Rocket.Chat intance, which parses the payload and then posts a message containing differen information.<br />
<br /><br /><br /><br />

## Installation <a name="installation"></a>

### Download code
Download source from [here][source].<br />
Unzip Sources.
<br /><br /><br />

### Configure Rocket.Chat

#### Add user (optional)
This step is optional if you've already got a user which you want to use as post author you can skip this step.<br />
Otherwise add a new user who is posting the updates to your channel or who ist texting the user which is supposed to be informed.
<br /><br />

#### Configure incoming Webhook in Rocket.Chat
In your Rocket.Chat instance go to administration panel an click on "Integrations". To add an integration with BitRocket click on "NEW INTEGRATION".<br />
Next, choose "Incoming WebHook".
<br />
Now, on the webhook config screen, set the following values:
<br /><br />

##### Enabled
Set this value to true
<br /><br />

##### Name (optional)
Enter the desired name for the integration (e.g. "BitRocket").
<br /><br />

##### Post to Channel
Self-explaining option. Insert the desired channel or user which receives the post on pushing to your repositories.<br />
An example user would be `@username`, an example channel would be `#channelname`.
<br /><br />

##### Post as
Here you've got to define the user who is posting the updates. This is the user you've created earlier.
<br /><br />

##### Script Enabled
Set this setting to true.
<br /><br />

##### Script

###### BitBucket Cloud
When using BitBucket Cloud you have to insert the complete code of the file `BBCloud__POSTReceiveHook.js` into this field.<br />
<br />

###### BitBucket Server
When using BitBucket Server you have to insert the complete code of the file `BBServer_POSTReceiveHook.js` into this field.<br />
<br /><br />

#### Save changes
Now click on "SAVE CHANGES" to get the required information (it is possible that you'll receive an empty error message below the "Script" option - just ignore it).
<br /><br /><br /><br />

### Configure BitBucket Cloud

#### Create Post-Receive WebHook in repository
Navigate to the desired repository and click on "Settings" in the left column.<br />
Now click on "Webhooks" and then on "Add webhook".<br />
The opening page provides an input field for defining your webhook title and your webhook url.<br />
Please enter the correct url to your Rocket.Chat webhook (just copy it from Rocket.Chat integration settings).<br />
On the "Triggers"-option select "Choose from a full list of triggers". In the following list check "Repository -> Push" and every option below "Pull Request"<br />
You can select everything here and overwrite this settings in the script-config directly inside of Rocket.Chat.
<br /><br />

##### Supported triggers
* Repository Events
    - Push
    - Fork
    - Commit Comment Created
    - ~~Commit Status Created~~ _(Example payload needed)_
    - ~~Commit Status Updated~~ _(Example payload needed)_
* Issue Events
    - ~~Created~~ _(Example payload needed)_
    - ~~Updated~~ _(Example payload needed)_
    - ~~Comment Created~~ _(Example payload needed)_
* Pull Request Events
    - Created
    - Updated
    - ~~Approved~~ _(BitBucket provides too less info)_
    - ~~Approval Removed~~ _(BitBucket provides too less info)_
    - Merged
    - Declined
    - Comment Created
    - Comment Updated
    - Comment Deleted
<br /><br />

Click on "Save" and your done!
<br /><br /><br /><br />

### Configure BitBucket Server

#### Install Post-Receive Webhook plugin
If it's not installed yet, you need to install the free [BitBucket Server Web Post Hooks Plugin][BitBucketplugin].<br />
To install the plugin login to your BitBucket Server instance an navigate to Administration and there click on "Find new add-ons" under section ADD-ONS.<br />
Search for `BitBucket Server Web Post Hooks Plugin` and click on install.
<br /><br />

#### Create Post-Receive WebHook in repository
Once the [BitBucket Server Web Post Hooks Plugin][BitBucketplugin] is installed, navigate to the desired repository and click on "Settings" in the left column.<br />
Now click on "Hooks" and enable "Post-Receive WebHooks".<br />
After enabling "Post-Receive WebHooks" klick on the little pen-icon next to the plugin title. The opening modal provides an input field for defining your webhook url.<br />
Please enter the correct url to your Rocket.Chat webhook (just copy it from Rocket.Chat integration settings).<br />
Click on "Save" and your done!
<br /><br /><br /><br />

### Test connection
To test wether communication between Bitbuket and Rocket.Chat works or not, just push any changes to the repository you've set up the hook.<br />
Did your channel or user receive a notification about the push? Congrats - everything is fine!<br />
No message received? Please double check all steps. If everything is set up as mentioned in this how to and it still doesn't work, feel free to drop us a line!
<br /><br /><br /><br />

## Add more repositories <a name="more"></a>
To inform your Rocket.Chat channel or user about changes on other repositories, just follow the instructions on how to create the Post-Receive WebHook in BitBucket Server again. You're not limited in the number of repositories which send information to Rocket.Chat. 
<br /><br /><br /><br />

## Want to contribute? <a name="contribute"></a>
If you have any ideas on how to make this script way better, feel free to contact us. We would love to add more features. Let's improve this work together!
<br /><br /><br /><br />

## Team <a name="team"></a>
Manuel Bachl (<m.bachl@finndrop.de>)<br />
Thies Schneider (<t.schneider@finndrop.de>)
<br /><br /><br /><br />

## Copyright & License <a name="license"></a>
![Finndrop Studios][finndroplogo]
<br />
Copyright (c) 2016 „[Finndrop Studios][finndrop]“
<br /><br />
Licensed under the [MIT license][license].

<!-- links -->
[BitBucketserver]: https://BitBucket.org/product/server "Atlassian BitBucket Server"
[BitBucketcloud]: https://BitBucket.org "Atlassian BitBucket Cloud"
[rocketchat]: https://rocket.chat/ "Rocket.Chat"
[BitBucketplugin]: https://marketplace.atlassian.com/plugins/com.atlassian.stash.plugin.stash-web-post-receive-hooks-plugin/server/overview "BitBucket Server Web Post Hooks Plugin"
[source]: https://git.finndrop-office.de/plugins/servlet/archive/projects/FDS/repos/bitrocket?at=refs%2Fheads%2Fmaster "Download BitRocket"
[finndrop]: https://www.finndrop.de "Finndrop Studios"
[license]: license/LICENSE-MIT.txt "MIT License"

<!-- images -->
[bitrocketlogo]: images/bitrocketlogo.png "Bitrocket logo"
[finndroplogo]: images/finndroplogo.png "Finndrop Studios"

