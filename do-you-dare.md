# Do you dare?

These are several challenges for you:

## Use Image builder to customize the image

We have customize the RHEL for Edge image using kickstart to perform different tasks:

1. User creation (**core**).
2. Public key configuration for the **core** user.
3. Firewall configuration.
4. Systemd units.

You can see them in the [kickstart file](ansible/roles/hypervisor/templates/edge.ks.j2).

> ![TIP](icons/tip-icon.png) The above is an ansible template file that will be rendered when it is deployed in the hypervisor to be included in the boot iso. You can see the rendered template in the hypervisor **/tmp/rheledge/edge.ks** or in the deployed RHEL Edge server in **/root/original-ks.cfg**.

Image Builder, the RHEL service we have used to create the RHEL for Edge images can be used to customize RHEL images in more ways that only add RPM packages in the image. 

Use Image Builder service to customize as much as possible the image, remove the customizations from the kickstart and redeploy the RHEL for Edge server.

> ![TIP](icons/tip-icon.png) Make a backup for the original kickstart, just in case ;-).

> ![TIP](icons/tip-icon.png) You can find more information about using Image Builder in RHEL official documentation [Composing a customized RHEL system image.](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/composing_a_customized_rhel_system_image/index)

## Use Image builder to create the installation ISO

In this workshop we have deployed the image creating a boot iso to deploy the RHEL for Edge Server but the Image builder service can be used to create the iso for installation or installing using an USB. 

Use Image Builder service to create ISO and USB installers and deploy the RHEL for Edge server using them.

> ![TIP](icons/tip-icon.png) You can find a bit more of information in RHEL official documentation [Composing, installing, and managing RHEL for Edge images.](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/composing_installing_and_managing_rhel_for_edge_images/index)

