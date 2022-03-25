Tag Types
=========

Tag functions have been upgraded on the platform. After the upgrade, a tag consists of a key and a value. Keys and values comply with the following rules:

-  For the tags created after the upgrade, all characters in **tags** are automatically used as a key, and the value is empty. Tags consist of only digits, letters, hyphens (-), and underscores (_).
-  For the tags that have been created before the upgrade:

   -  If no period (.) is used in **tags**, all characters in **tags** are used as a key, and the value is empty.
   -  If periods (.) are used in **tags**, the characters before the first period are used as a key and the characters after the first period are used as a value.

After the tag function upgrade, tag management APIs are classified as the APIs for 1D tags and the APIs for 2D tags.

-  A 1D tag contains a string. All APIs for 1D tags are native OpenStack APIs. For details, see this section.
-  A 2D tag consists of a key and a value. All APIs for 2D tags are ECS APIs. For details, see `Tag Management <../../apis_recommended/tag_management/index.html>`__.

.. note::

   -  You are advised to use the APIs of the same type to add, delete, modify, or query tags.
   -  You are advised to use 2D tags.


