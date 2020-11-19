*HDP-TIH - Advanced Dependency Condition*
=============


Adds advanced conditions for uproc jobs.
http://github.com/Automic-Community/HDP-TIH---Advanced-Dependency-Condition

<!-- List of attached files -->
Contents of Solution Package:

						
								*tih_advanced_dependency_v2.txt.zip
								
						


Documenation and Instructions
---

<p><strong class="bbc">ENGLISH DESCRIPTION :</strong><br />In $U, dependency condition on HDP uproc only offers 2 options : "<strong class="bbc"><em class="bbc">All required</em></strong>" and "<em class="bbc"><strong class="bbc">One is enough</strong></em>"<br /><br /></p>
<p><strong class="title">Target environments:</strong> Any perl environment</p>
<p><strong class="title">Prerequisites:</strong> Any $U that can launch perl script</p>
<p><strong class="title">Implementation:</strong> This script is intended to be the code of the uproc</p>
<p><br />&nbsp;<br />This script, which must be the code of the conditioned uproc, allow to :<br /><br /><br /></p>
<p class="bbc_indent" style="margin-left: 40px;">- handle one or many HDP uprocs as dependencies conditions</p>
<p class="bbc_indent" style="margin-left: 40px;">- wait that all HDP uprocs are "COMPLETED" or "ABORTED"</p>
<p class="bbc_indent" style="margin-left: 40px;">- [OPTIONAL] : specify a minimum percentage of required "COMPLETED" uprocs. The percentage is global (whatever is the number of HDP uprocs)</p>
<p>&nbsp;<br />Functioning of the script :</p>
<p class="bbc_indent" style="margin-left: 40px;">1 - The script will analyze the T_TARGET&lt;N&gt; variables in order to verify if all uprocs and MUT exist</p>
<p class="bbc_indent" style="margin-left: 40px;">2 - Check every uproc status</p>
<p class="bbc_indent" style="margin-left: 40px;">3 - Wait 'N' seconds before doing a new check</p>
<p class="bbc_indent" style="margin-left: 40px;">4 - As soon as all uprocs will be "COMPLETED" or "ABORTED" (And if the value of the required percentage is different from zero), the script will calculate the percentage of "COMPLETED" uproc and determine its own status ("COMPLETED" or "ABORTED")</p>
<p>&nbsp;<br />Setup :<br />Paste the content of the text file as the end session' uproc content (CL_INT). The end session uproc should be set as a OK son of the header uproc.<br /><br />&nbsp;<br />Uproc' variables :</p>
<p class="bbc_indent" style="margin-left: 40px;">- <strong class="bbc">T_WAIT </strong>: waiting time between each check (seconds)</p>
<p class="bbc_indent" style="margin-left: 40px;">- <strong class="bbc">T_PERCENT</strong> : minimum percentage of "COMPLETED" uproc required</p>
<p class="bbc_indent" style="margin-left: 40px;">- <strong class="bbc">T_TARGET&lt;N&gt;</strong> (N going from 0 to N) : couple &lt;Uproc/Management Unit Type) to monitore. Format : &lt;UPROC&gt;;&lt;MUT&gt;</p>
<p><br />&nbsp;<br />NOTES :&nbsp;<br />1 ) At each check run, the script will write into the job log which uproc is not yet "COMPLETED" or "ABORTED".<br />If you want to remove this feature, you just have to delete / comment line 64.<br /><br />&nbsp;<br />2 ) Variables T_TARGET&lt;N&gt; must begin with N equal to 0. Figures have to follow itself.<br />&nbsp;<br />====================================================================================<br /><strong class="bbc">DESCRIPTION EN FRANCAIS :</strong><br />Dans $U, la gestion des conditions d'enchainement sur une uproc en TIH n'offre que 2 options : "<strong class="bbc">Toutes n&eacute;cessaires</strong>" et "<strong class="bbc">Une suffisante</strong>"<br /><br />Ce script, plac&eacute; dans le code de l'uproc qui doit avoir cette condition d'enchainement, permet de :</p>
<p class="bbc_indent" style="margin-left: 40px;">- conditionner de 1 &agrave; N uproc tournant en TIH</p>
<p class="bbc_indent" style="margin-left: 40px;">- d'attendre que toutes les uprocs en TIH soient au status "COMPLETED" ou "ABORTED"</p>
<p class="bbc_indent" style="margin-left: 40px;">- [OPTIONNEL] : de sp&eacute;cifier un pourcentage minimun global requis (au cas ou plusieurs uprocs en TIH soient attendues) d'uproc au status "COMPLETED"</p>
<p>&nbsp;<br />Fonctionnement du script :</p>
<p class="bbc_indent" style="margin-left: 40px;">1 - Le script va analyser les variables contenant les couples &lt;Uproc/Type d'unit&eacute; de gestion&gt; &agrave; surveiller afin de v&eacute;rifier que les Uprocs et les MUT existent bien</p>
<p class="bbc_indent" style="margin-left: 40px;">2 - Controler pour chaque Uproc son status</p>
<p class="bbc_indent" style="margin-left: 40px;">3 - Attendre 'N' secondes avant de refaire un contr&ocirc;le</p>
<p class="bbc_indent" style="margin-left: 40px;">4 - Quand toutes les uprocs seront en "COMPLETED" ou "ABORTED" (et si un pourcentage est sp&eacute;cifi&eacute;), calculer le pourcentage d'uproc en "COMPLETED" et d&eacute;terminer son status ("COMPLETED" ou "ABORTED") selon le r&eacute;sultat</p>
<p>&nbsp;<br />Mise en place :<br />Copier le contenu du fichier dans le code l'uproc de fin de la session et la mettre comme fils normal de l'uproc d'en-t&ecirc;te<br /><br />&nbsp;<br />Variables d'uproc :</p>
<p class="bbc_indent" style="margin-left: 40px;">- <strong class="bbc">T_WAIT</strong> : temps d'attente entre chaque v&eacute;rification (en secondes)</p>
<p class="bbc_indent" style="margin-left: 40px;">- <strong class="bbc">T_PERCENT</strong> : pourcentage d'uproc en "COMPLETED" requis</p>
<p class="bbc_indent" style="margin-left: 40px;">- <strong class="bbc">T_TARGET&lt;N&gt;</strong> (N allant de 0 &agrave; N) : couple &lt;Uproc/Type d'unit&eacute; de gestion) &agrave; surveiller. Format : &lt;UPROC&gt;;&lt;MUT&gt;4</p>
<p><br />&nbsp;<br />NOTES :&nbsp;<br />1 ) le script indique pour chaque contr&ocirc;le, quelles sont les uprocs qui ne sont pas au status "COMPLETED" ou "ABORTED".<br />Si vous souhaitez d&eacute;sactiver cette fonction, il suffit de supprimer / commenter la ligne 64 du script.<br /><br />2 ) Les variables T_TARGET&lt;N&gt; doivent se suivre et commencer &agrave; 0. Il ne doit pas y avoir de trou dans la num&eacute;rotation.</p>

Copyright and License
---

Broadcom does not support, maintain or warrant Solutions, Templates, Actions and any other content published on the Community and is subject to Broadcom Community [Terms and Conditions](https://community.broadcom.com/termsandconditions)


Questions or Need Help? 
---
Join the [Automic Community Integrations](https://community.broadcom.com/communities/community-home?CommunityKey=83e49dd4-b93e-464a-a343-2bb1e51c13ec) to discuss this integration.
