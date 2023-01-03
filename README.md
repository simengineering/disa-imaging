Custom image built by Jenkins.


This job is triggered by the weekly Oracle base-image checker job located in support-files/custom-image/ci/check-for-latest-image.Jenkinsfile. The image-checker runs Sunday around midnight EST. If the checker determines Oracle has released a new base-image, this image builder will be started. This job is called by the checker using 'main' as the branch. 'Main' is currently configured
as the default builder, running oracle linux 7.9. See * Note: @ bottom for information on other branches.
When this job runs, the main branch will build a custom hardened linux image from the latest 7.9 Oracle Linux release.
The job spawns an instance in the cmns-dev compartment and proceeds to run ansible playbooks and custom scripts to create a DISA compliant image.
Distribution:
After the image is created it is available in cmnsvcdply-znc custom-images.
Additionally, the image is exported to many other zones.
Related Jobs:
Per security regulations, zna and prod must pull from znb, therefore the image checker job runs separately in zna and prod, polling znb artifactory for a new release. If a new image has been built, it is imported directly from the znb custom-image-bucket-znb to custom images.

Note:

Branch ol8-min-disa will perform the same task(s), but for Oracle Linux 8.6.
Branch oke-min-disa will perform the same task(s), but for the latest OKE image.
