---
title: Settings
---

## Show or hide all summaries on list pages

<!-- Todo: menu link for summaries, just like other toggles -->

By default list pages show summaries for all the studies they link to. This is advantageous since you can use these to get an idea of what each study is about, but disadvantageous in that fewer overall links can be displayed at once. If you would prefer to have the summaries hidden by default (although still viewable on a link-by-link basis by clicking on the plus button to the right of any link's title), you can select such below.

While you can always go back and forth between showing summaries and hiding summaries for an individual list page using the page-level link found in the menu sidebar, most users will probably mostly be interested in having the same summary visibility preference active across list pages. For this reason, you can set the visibility option here globally, and all list pages across the site will then default to your chosen summary visibility setting.

<div id="summariesPreferenceContainer" class="settingsContainer">
	<div id="summariesPreferenceDisplay"></div>
	<div><input id="embedded" onclick="javascript:toShowingSummariesOption();" type="button" value="View summaries on list pages" /></div>
	<div><input id="plaintext" onclick="javascript:toHidingSummariesOption();" type="button" value="Hide summaries on list pages" /></div>
</div>

<style>
	.settingsContainer {
		border: 1px solid black;
		border-radius: 5px;
	}
	
	.settingsContainer > div {
		padding: 10px;
	}

	.settingsContainer {
		font-weight: bold;
	}

	#summariesContainer input {
		width: 300px;
	}
</style>

Keep in mind that if you clear your browser cookies, your preferences here will be lost, and you'll have to select them again.


## Reftagger settings

You can use the below control panel to change settings relating to the verse tagging used on this site. Of particular note, you can change the Bible version used, as well as toggle whether or not you include links to Logos Bible Software in the tagging. If you do, clicking on the L in the box next to a link will open the tagged passage in Logos. This is very useful if you are a user of Logos (but if you are not, it reduces visual clutter to disable this option, which is why it is off by default).

<!-- Reftagger Control Panel -->
<div id="lbsRefTaggerCP" style="border: 1px solid black; border-radius: 5px;">
	<div id="lbsHeader" style="padding: 10px;">
		<a href="https://faithlife.com/products/reftagger">Bible Options</a>
	</div>
	<div id="lbsVersionContainer" style="padding: 10px;">
		<select id="lbsVersion">
			<option value="AB">AMP</option>
			<option value="ASV">ASV</option>
			<option value="DAR">DARBY</option>
			<option value="ESV">ESV</option>
			<option value="GW">GW</option>
			<option value="HCSB">HCSB</option>
			<option value="KJV">KJV</option>
			<option value="LEB">LEB</option>
			<option value="MESSAGE">MESSAGE</option>
			<option value="NASB">NASB</option>
			<option value="NCV">NCV</option>
			<option value="NIV">NIV</option>
			<option value="NIRV">NIRV</option>
			<option value="NKJV">NKJV</option>
			<option value="NLT">NLT</option>
			<option value="TNIV">TNIV</option>
			<option value="YLT">YLT</option>
		</select>
	</div>
	<div id="lbsLibronixContainer" style="padding: 10px;">
		<input id="lbsUseLibronixLinks" type="checkbox"/>
		<label for="lbsUseLibronixLinks">Show Logos Links</label>
	</div>
	<div id="lbsSaveContainer" style="padding: 10px;">
		<input id="lbsSave" onclick="javascript:refTagger.lbsSavePrefs()" type="button" value="Save" />
	</div>
</div>
<!-- End RefTagger Control Panel. For more info visit https://faithlife.com/products/reftagger. -->

Keep in mind that if you clear your browser cookies, your preferences here will be lost, and you'll have to select them again.


<script type="text/javascript">
	function setCookie(cname,cvalue,exdays) {
	  var d = new Date();
	  d.setTime(d.getTime() + (exdays*24*60*60*1000));
	  var expires = "expires=" + d.toGMTString();
	  document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
	}

	function getCookie(cname) {
	  var name = cname + "=";
	  var decodedCookie = decodeURIComponent(document.cookie);
	  var ca = decodedCookie.split(';');
	  for(var i = 0; i < ca.length; i++) {
		var c = ca[i];
		while (c.charAt(0) == ' ') {
		  c = c.substring(1);
		}
		if (c.indexOf(name) == 0) {
		  return c.substring(name.length, c.length);
		}
	  }
	  return "";
	}
	
	function toShowingSummariesOption() {
		setCookie('summariesPreference', 'show', 1825);
		displaySummariesPreference();
	}

	function toHidingSummariesOption() {
		setCookie('summariesPreference', 'hide', 1825);
		displaySummariesPreference();
	}

	function displaySummariesPreference() {
		var summariesPreference=getCookie("summariesPreference");
		var displayDiv = document.getElementById("summariesPreferenceDisplay");
		if(summariesPreference == "show")
		{
			displayDiv.innerHTML = "Current summaries display setting: show summaries";
		}
		else if(summariesPreference == "hide")
		{
			displayDiv.innerHTML = "Current summaries display setting: hide summaries";
		}
		// if user hasn't set cookie, set cookie and show summaries
		else { // summariesPreference = ""
			setCookie('summariesPreference', 'show', 1825);
			displayDiv.innerHTML = "Current summaries display setting: show summaries";
		}
	}
	
	displaySummariesPreference();
</script>
