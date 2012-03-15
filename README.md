Venus on OpenShift
=========================
Venus is an awesome ‘river of news’ feed reader. It downloads news feeds published by web sites and aggregates their content together into a single combined feed, latest news first.

More information can be found at http://intertwingly.net/code/venus/docs/index.html.

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a PHP application

	rhc app create -a venus -t php-5.3

Add cron support to your application
    
	rhc app cartridge add -a venus -c cron-1.4
    
Add this upstream Venus quickstart repo

	cd venus
	rm php/index.php
	git remote add upstream -m master git://github.com/jasonbrooks/venus-openshift-quickstart.git
	git pull -s recursive -X theirs upstream master

Then push the repo upstream to OpenShift

	git push        

That's it, you can now checkout your application at:

	http://venus-$yourdomain.rhcloud.com
