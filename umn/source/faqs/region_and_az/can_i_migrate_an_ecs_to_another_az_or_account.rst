:original_name: en-us_topic_0236308363.html

.. _en-us_topic_0236308363:

Can I Migrate an ECS to Another AZ, or Account?
===============================================

After an ECS is created, it cannot be directly migrated to another AZ, or account.

To migrate ECSs across AZs or accounts, you can use Image Management Service (IMS) to create private images, replicate images, and share images. The process is as follows:

#. Creates a private image using the ECS.

   -  If cross-AZ migration is required, replicate the private image to another AZ.
   -  If cross-account migration is required, share private images with other accounts.

#. Create an ECS using the private image.

For details, see the *Image Management Service User Guide*.
