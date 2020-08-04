---
title: SOS.dll (Extension de débogage SOS)
description: Utilisez SOS.dll, l’extension de débogage SOS. Déboguez des programmes managés dans Visual Studio et dans WinDbg.exe en obtenant des informations sur l’environnement CLR interne.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
ms.openlocfilehash: cc9fed8432b5b24c20c3c470a842895a901d9efb
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517176"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (extension de débogage SOS)

L’extension de débogage SOS (SOS.dll) vous aide à déboguer des programmes managés dans le débogueur Windows (WinDbg.exe) et dans Visual Studio en vous fournissant des informations sur l’environnement interne du CLR (Common Language Runtime). Cet outil requiert l'activation du débogage non managé pour votre projet. SOS.dll est installé automatiquement avec .NET Framework. Pour utiliser SOS.dll dans Visual Studio, installez le [Kit WDK (Windows Driver Kit)](/windows-hardware/drivers/download-the-wdk).

## <a name="syntax"></a>Syntax

```console
![command] [options]
```

## <a name="commands"></a>Commandes

|Commande|Description|
|-------------|-----------------|
|**AnalyzeOOM** (**ao**)|Affiche les informations pour le dernier événement Mémoire insuffisante (OOM) qui s’est produit sur une demande d’allocation au tas de garbage collection. (Dans le garbage collection côté serveur, il affiche OOM, le cas échéant, sur chaque tas de garbage collection.)|
|**BPMD** [**-nofuturemodule**] [ \<*module name*> \<*method name*> ] [**-MD**  < `MethodDesc`>] **-List** **-Clear** \<*pending breakpoint number*> **-ClearAll**|Crée un point d'arrêt sur la méthode spécifiée dans le module spécifié.<br /><br /> Si le module et la méthode spécifiés n'ont pas été chargés, cette commande attend une notification indiquant que le module a été chargé et compilé juste-à-temps avant de créer un point d'arrêt.<br /><br /> Vous pouvez gérer la liste de points d’arrêt en attente à l’aide des options **-list**, **-clear** et **-clearall** :<br /><br /> L’option **-list** génère une liste de tous les points d’arrêt en attente. Si un point d'arrêt en attente a un ID de module non nul, ce point d'arrêt est spécifique à une fonction dans ce module spécifique chargé. Si le point d'arrêt en attente a un ID de module nul, ce point d'arrêt s'applique aux modules qui n'ont pas encore été chargés.<br /><br /> Utilisez l’option **-clear** ou **-clearall** pour supprimer des points d’arrêt en attente dans la liste.|
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Fournit uniquement une trace de la pile du code managé.<br /><br /> L’option **-p** fournit les arguments à la fonction managée.<br /><br /> L’option **-l** fournit des informations sur les variables locales dans un frame. L’extension de débogage SOS ne peut pas récupérer les noms locaux, donc la sortie pour les noms locaux est au format \<*local address*> **=** \<*value*> .<br /><br /> L’option **-a**(tout) est un raccourci de la combinaison de **-l** et **-p**.<br /><br /> L’option **-n** désactive l’affichage des noms de fichier source et des numéros de ligne. Si l'option SYMOPT_LOAD_LINES est spécifiée sur le débogueur, SOS recherche les symboles pour chaque frame managé et, s'il les trouve, affiche le nom de fichier source et le numéro de ligne correspondants. Le paramètre **-n** (aucun numéro de ligne) peut être spécifié pour désactiver ce comportement.<br /><br /> L’extension de débogage SOS n’affiche pas de frames de transition sur les plateformes x64 et IA-64.|
|**COMState**|Répertorie le modèle cloisonné COM pour chaque thread et un pointeur `Context`, si disponible.|
|**DumpArray** [**-Start** \<*startIndex*> ] [**-Length** \<*length*> ] [**-Details**] [**-nofields**]\<*array object address*><br /><br /> -ou-<br /><br /> **Da** [**-Start** \<*startIndex*> ] [**-longueur** \<*length*> ] [**-Detail**] [**-nofields**] *tableau-adresse d’objet*>|Examine les éléments d'un objet tableau.<br /><br /> L’option **-start** spécifie l’index de départ à partir duquel les éléments doivent être affichés.<br /><br /> L’option **-length** spécifie le nombre d’éléments à afficher.<br /><br /> L’option **-details** affiche les détails de l’élément en utilisant les formats **DumpObj** et **DumpVC**.<br /><br /> L’option **-nofields** empêche l’affichage des tableaux. Cette option est disponible uniquement quand l’option **-detail** est spécifiée.|
|**DumpAssembly**\<*assembly address*>|Affiche des informations concernant un assembly.<br /><br /> La commande **DumpAssembly** répertorie plusieurs modules, s’ils existent.<br /><br /> Vous pouvez obtenir une adresse d’assembly à l’aide de la commande **DumpDomain**.|
|**DumpClass**\<*EEClass address*>|Affiche des informations sur la structure `EEClass` associée à un type.<br /><br /> La commande **DumpClass** affiche des valeurs de champ static, mais pas les valeurs de champ non static.<br /><br /> Utilisez la commande **DumpMT**, **DumpObj**, **Name2EE** ou **Token2EE** pour obtenir une adresse de structure `EEClass`.|
|**DumpDomain** [ \<*domain address*> ]|Répertorie chaque objet <xref:System.Reflection.Assembly> chargé dans l'adresse d'objet <xref:System.AppDomain> spécifiée.  En cas d’appel sans paramètres, la commande **DumpDomain** répertorie tous les objets <xref:System.AppDomain> dans un processus.|
|**Dumpheap** [**-Stat**] [**-Strings**] [**-short**] [**-min** \<*size*> ]**[-Max** \<*size*> ] [**-thinlock**] [**-startAtLowerBound**] [**-MT** \<*MethodTable address*> ] [**-type** \<*partial type name*> ] [*Start* [*end*]]|Affiche des informations sur le tas récupéré par le récupérateur de mémoire et des statistiques de collection concernant les objets.<br /><br /> La commande **DumpHead** affiche un avertissement si elle détecte une fragmentation excessive dans le tas de récupérateur de mémoire.<br /><br /> L’option **-stat** restreint la sortie au récaptitulatif de type statistique.<br /><br /> L’option **-string** restreint la sortie à un récapitulatif de la valeur de la chaîne statistique.<br /><br /> L’option **-short** limite la sortie à l’adresse de chaque objet. Cela vous permet de canaliser facilement une sortie depuis la commande vers une autre commande de débogueur pour l'automation.<br /><br /> L’option **-min** ignore les objets inférieurs au paramètre `size`, spécifié en octets.<br /><br /> L’option **-max** ignore les objets inférieurs au paramètre `size`, spécifié en octets.<br /><br /> L’option **-thinlock** indique ThinLocks.  Pour plus d’informations, consultez la commande **SyncBlk**.<br /><br /> L'option `-startAtLowerBound` force le parcours du segment de mémoire à commencer à la limite inférieure d'une plage d'adresses fournie. Pendant la phase de planification, le tas n'est pas souvent opérationnel parce que des objets sont déplacés. Cette option force **DumpHead** à commencer son parcours à la limite inférieure spécifiée. Vous devez fournir l'adresse d'un objet valide comme limite inférieure pour que cette option fonctionne. Vous pouvez afficher la mémoire à l'adresse d'un mauvais objet pour rechercher manuellement la table de méthodes suivante. Si le garbage collection est actuellement en communication avec `memcopy`, vous pouvez également rechercher l'adresse de l'objet suivant en ajoutant la taille à l'adresse de démarrage, qui est fournie comme paramètre.<br /><br /> L’option **-mt** répertorie uniquement les objets qui correspondent à la structure `MethodTable` spécifiée.<br /><br /> L’option **-type** répertorie uniquement les objets dont le nom de type correspond à une sous-chaîne de la chaîne spécifiée.<br /><br /> Le paramètre `start` commence à répertorier les éléments à partir de l'adresse spécifiée.<br /><br /> Le paramètre `end` cesse de répertorier les éléments à l'adresse spécifiée.|
|**DumpIL** \<*Managed DynamicMethod object*> &#124; \<*DynamicMethodDesc pointer*> &#124;\<*MethodDesc pointer*>|Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée.<br /><br /> Notez que le langage MSIL dynamique est émis différemment du langage MSIL chargé à partir d'un assembly. Le langage MSIL dynamique fait référence aux objets d'un tableau d'objets managés plutôt qu'aux jetons de métadonnées.|
|**DumpLog** [**-addr** \<*addressOfStressLog*> ] [<*Filenam* `e`>]|Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié. Si vous ne spécifiez pas de nom, cette commande crée un fichier appelé StressLog.txt dans le répertoire actif.<br /><br /> Le journal de contrainte en mémoire vous aide à diagnostiquer les échecs de contrainte sans utiliser de verrous ou d'E/S. Pour activer le journal de contrainte, définissez les clés de Registre suivantes sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework :<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> L'option `-addr` facultative vous permet de spécifier un journal de contrainte autre que le journal par défaut.|
|**DumpMD**\<*MethodDesc address*>|Affiche des informations sur une structure `MethodDesc` à l'adresse spécifiée.<br /><br /> Vous pouvez utiliser la commande **IP2MD** pour obtenir l’adresse de structure `MethodDesc` d’une fonction managée.|
|**DumpMT** [**-MD**]\<*MethodTable address*>|Affiche des informations sur une table de méthodes à l'adresse spécifiée. Quand l’option **-MD** est spécifiée, une liste de toutes les méthodes définies avec l’objet s’affiche.<br /><br /> Chaque objet managé contient un pointeur de table de méthodes.|
|**DumpMethodSig** \<*sigaddr*> DumpMethodSig  < *moduleadd*`r`>|Affiche des informations sur une structure `MethodSig` à l'adresse spécifiée.|
|**DumpModule** [**-MT**]\<*Module address*>|Affiche des informations sur un module à l'adresse spécifiée. L’option **-mt** affiche les types définis dans un module et les types référencés par le module<br /><br /> Vous pouvez utiliser la commande **DumpDomain** ou **DumpAssembly** pour récupérer l’adresse d’un module.|
|**DumpObj** [**-nofields**]\<*object address*><br /><br /> -ou-<br /><br /> **DO** \<*object address*>|Affiche des informations sur un objet à l'adresse spécifiée. La commande **DumpObj** affiche les champs, les informations de la structure `EEClass`, la table de méthodes et la taille de l’objet.<br /><br /> Vous pouvez utiliser la commande **DumpStackObjects** pour récupérer l’adresse d’un objet.<br /><br /> Notez que vous pouvez exécuter la commande **DumpObj** dans les champs de type `CLASS`, car ce sont également des objets.<br /><br /> L’option `-`**nofields** empêche l’affichage des champs de l’objet, ce qui est utile pour des objets comme String.|
|**DumpRuntimeTypes**|Affiche les objets de type au moment de l'exécution dans le tas de récupérateur de mémoire et répertorie leurs noms de types et tables de méthodes associés.|
|**DumpStack** [**-EE**] [**-n**] [ `top` *Stack* [ `bottom` *STAC* `k` ]]|Affiche une trace de la pile.<br /><br /> Quand l’option **-EE** est spécifiée, la commande **DumpStack** affiche uniquement les fonctions managées. Utilisez les paramètres `top` et `bottom` pour limiter les frames de pile affichés sur les plateformes x86.<br /><br /> L’option **-n** désactive l’affichage des noms de fichier source et des numéros de ligne. Si l'option SYMOPT_LOAD_LINES est spécifiée sur le débogueur, SOS recherche les symboles pour chaque frame managé et, s'il les trouve, affiche le nom de fichier source et le numéro de ligne correspondants. Le paramètre **-n** (aucun numéro de ligne) peut être spécifié pour désactiver ce comportement.<br /><br /> Sur les plateformes x86 et x64, la commande **DumpStack** crée une trace de pile détaillée.<br /><br /> Sur les plateformes IA-64, la commande **DumpStack** reproduit la commande **K** du débogueur. Les paramètres `top` et `bottom` sont ignorés sur les plateformes IA-64.|
|**DumpSig** \<*sigaddr*>\<*moduleaddr*>|Affiche des informations sur une structure `Sig` à l'adresse spécifiée.|
|**DumpSigElem** \<*sigaddr*>\<*moduleaddr*>|Affiche un élément unique d'un objet de signature. Dans la plupart des cas, vous devez utiliser **DumpSig** pour examiner des objets de signature individuels. Toutefois, si une signature est endommagée, vous pouvez utiliser **DumpSigElem** pour lire ses parties valides.|
|**DumpStackObjects** [**-verify**] [ `top` *pile* [ `bottom` *Stack*]]<br /><br /> -ou-<br /><br /> **DSO** [**-verify**] [ `top` *pile* [ `bottom` *Stack*]]|Affiche tous les objets managés recherchés dans les limites de la pile actuelle.<br /><br /> L’option **-verify** valide chaque champ `CLASS` non static d’un champ d’objet.<br /><br /> Utilisez la commande **DumpStackObject** avec les commandes de traçage de la pile, comme la commande **K** et la commande **CLRStack**, pour déterminer les valeurs des variables et paramètres locaux.|
|**DumpVC** \<*MethodTable address*>\<*Address*>|Affiche des informations sur les champs d'une classe de valeur à l'adresse spécifiée.<br /><br /> Le paramètre **MethodTable** permet à la commande **DumpVC** d’interpréter correctement les champs. Les classes de valeur ne disposent pas d'une table de méthodes comme premier champ.|
|**EEHeap** [**-gc**] [**-loader**]|Affiche des informations sur la mémoire du processus consommée par les structures de données internes du CLR.<br /><br /> Les options **-gc** et **-loader** limitent la sortie de cette commande aux structures de données du récupérateur de mémoire ou du chargeur.<br /><br /> Les informations pour le récupérateur de mémoire répertorient les plages de chaque segment dans le tas managé.  Si le pointeur se trouve dans une plage de segments spécifiée par **-gc**, il s’agit d’un pointeur d’objet.|
|**EEStack** [**-short**] [**-EE**]|Exécute la commande **DumpStack** sur tous les threads dans le processus.<br /><br /> L’option **-EE** est passée directement à la commande **DumpStack**. Le paramètre **-short** limite la sortie aux types de threads suivants :<br /><br /> Threads avec un verrou.<br /><br /> Threads bloqués pour permettre un garbage collection.<br /><br /> Threads se trouvant actuellement dans le code managé.|
|**EEVersion**|Affiche la version du CLR.|
|**EHInfo** [ \<*MethodDesc address*> ] [ \<*Code address*> ]|Affiche les blocs de gestion des exceptions dans une méthode spécifiée.  Cette commande affiche les adresses de code et les offsets du bloc de clause (bloc `try`) et du bloc de gestionnaire (bloc `catch`).|
|**FORUM AUX QUESTIONS**|Affiche les questions fréquemment posées.|
|**FinalizeQueue** [**-detail**] &#124; [**-allReady**] [**-short**]|Affiche tous les objets enregistrés pour la finalisation.<br /><br /> L’option **-detail** affiche des informations supplémentaires sur les `SyncBlocks` qui doivent être nettoyés, ainsi que sur les `RuntimeCallableWrappers` (RCW) en attente de nettoyage. Ces deux structures de données sont mises en cache et nettoyées par le thread finaliseur lorsqu'il est exécuté.<br /><br /> L'option `-allReady` affiche tous les objets prêts pour la finalisation, qu'ils soient déjà marqués comme tel par le garbage collection ou qu'ils le soient par le garbage collection suivant. Les objets qui ne figurent pas dans la liste "prêt pour la finalisation" sont des objets finalisables qui ne sont plus associés à une racine. Cette option peut s'avérer très coûteuse, car elle vérifie si tous les objets des files d'attente finalisables sont toujours associés à une racine.<br /><br /> L'option `-short` limite la sortie à l'adresse de chaque objet. Si elle est utilisée conjointement à **-allReady**, elle énumère tous les objets qui ont un finaliseur qui n’est plus associé à une racine. S'il est utilisé indépendamment, il répertorie tous les objets dans les files d'attente finalisables et "prêtes pour la finalisation".|
|**FindAppDomain**\<*Object address*>|Détermine le domaine d'application d'un objet à l'adresse spécifiée.|
|**FindRoots** **-GEN** \<*N*> &#124; **-GEN any** &#124;\<*object address*>|Provoque l’arrêt du débogueur dans l’élément débogué sur la collection suivante de la génération spécifiée. L'effet est réinitialisé dès que l'arrêt se produit. Pour arrêter la collection suivante, vous devez rééditer la commande. La *\<object address>* forme de cette commande est utilisée après l’arrêt provoqué par la **génération** ou la **génération d’une** erreur. À cet instant, l’élément débogué est dans l’état nécessaire pour que **FindRoots** identifie des racines pour les objets à partir des générations condamnées actuelles.|
|**GCHandles** [**-perdomain**]|Affiche des statistiques sur les handles du récupérateur de mémoire dans le processus.<br /><br /> L’option **-perdomain** organise les statistiques par domaine d’application.<br /><br /> Utilisez la commande **GCHandles** pour rechercher les fuites de mémoire provoquées par les fuites du handle du récupérateur de mémoire. Par exemple, une fuite de mémoire se produit lorsque le code conserve un grand tableau, car un handle fort du récupérateur de mémoire pointe encore sur ce dernier ; le handle est ignoré sans libérer le tableau.|
|**GCHandleLeaks**|Recherche dans la mémoire des références à des handles forts et épinglés du récupérateur de mémoire dans le processus et affiche les résultats. Si un handle est trouvé, la commande **GCHandleLeaks** affiche l’adresse de la référence. Si aucun handle n'est trouvé dans la mémoire, cette commande affiche une notification.|
|**Gcinfo**\<*MethodDesc address*>\<*Code address*>|Affiche les données spécifiant les registres ou les emplacements de pile contenant des objets managés. Si un garbage collection a lieu, le collector doit connaître les emplacements des références aux objets pour pouvoir les mettre à jour avec les nouvelles valeurs de pointeur d’objet.|
|**Gcroot** [**-nopiles**]\<*Object address*>|Affiche des informations sur les références (ou racines) à un objet à l'adresse spécifiée.<br /><br /> La commande **GCRoot** examine le tas managé tout entier et la table des handles d’autres objets et des handles de la pile. Une recherche des pointeurs vers les objets est ensuite réalisée dans chaque pile et dans la file d'attente du finaliseur.<br /><br /> Cette commande ne détermine pas si la racine d'une pile est valide ou ignorée. Utilisez les commandes **CLRStack** et **U** pour désassembler le frame auquel appartient la valeur locale ou d’argument, pour déterminer si la racine d’une pile est encore utilisée.<br /><br /> L’option **-nostacks** restreint la recherche aux handles du récupérateur de mémoire et aux objets accessibles.|
|**GCWhere**  *\<object address>*|Affiche l’emplacement et la taille dans le tas de garbage collection de l’argument passé. Lorsque l’argument se trouve dans le tas managé, mais n’est pas une adresse d’objet valide, la taille s’affiche en tant que 0 (zéro).|
|**aide** [ \<*command*> ] [ `faq` ]|Affiche toutes les commandes disponibles lorsque aucun paramètre n'est spécifié ou affiche des informations d'aide détaillées sur la commande spécifiée.<br /><br /> Le paramètre `faq` affiche les réponses aux questions fréquentes.|
|**HeapStat** [**-inclUnrooted** &#124; **-iu**]|Affiche les tailles de génération pour chaque tas et l'espace libre total dans chaque génération sur chaque tas. Si l’option -**inclUnrooted** est spécifiée, le rapport inclut des informations sur les objets managés du tas de garbage collection qui n’est plus associé à une racine.|
|**HistClear**|Libère toutes les ressources utilisées par la famille de commandes `Hist`.<br /><br /> En général, vous n'avez pas à appeler `HistClear`explicitement, parce que chaque `HistInit` nettoie les ressources précédentes.|
|**HistInit**|Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.|
|**HistObj***\<obj_address>*|Examine tous les enregistrements de réadressage du journal de contrainte et affiche la chaîne des réadressages de garbage collection qui ont pu mener à l’adresse passée comme un argument.|
|**HistObjFind**  *\<obj_address>*|Affiche toutes les entrées de journal qui référencent un objet à l'adresse spécifiée.|
|**HistRoot***\<root>*|Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.<br /><br /> La valeur racine peut être utilisée pour suivre le déplacement d’un objet dans les garbage collections.|
|**IP2MD**\<*Code address*>|Affiche la structure `MethodDesc` à l'adresse spécifiée dans le code compilé juste-à-temps (JIT).|
|`ListNearObj` (`lno`) *\<obj_address>*|Affiche les objets précédant et suivant l'adresse spécifiée. La commande recherche dans le tas de garbage collection l’adresse qui ressemble à un début valide d’objet managé (selon une table de méthodes valide), ainsi que l’objet qui suit l’adresse d’argument.|
|**MinidumpMode** [**0**] [**1**]|Empêche l'exécution de commandes potentiellement dangereuses lors de l'utilisation d'un minidump.<br /><br /> Passez **0** pour désactiver cette fonctionnalité ou **1** pour l’activer. Par défaut, la valeur de **MinidumpMode** est **0**.<br /><br /> Les minidumps créés avec la commande **.dump /m** ou **.dump** ont des données propres à CLR limitées et vous permettent uniquement d’exécuter correctement un sous-ensemble de commandes SOS. Certaines commandes peuvent échouer avec des erreurs inattendues, car des zones de mémoire requises ne sont pas mappées ou ne sont mappées que partiellement. Cette option vous empêche d'exécuter des commandes potentiellement dangereuses dans les minidumps.|
|**Name2EE** \<*module name*>\<*type or method name*><br /><br /> -ou-<br /><br /> **Name2EE** \<*module name*> **!**\<*type or method name*>|Affiche la structure `MethodTable` et la structure `EEClass` pour le type ou la méthode spécifié dans le module spécifié.<br /><br /> Le module spécifié doit être chargé dans le processus.<br /><br /> Pour obtenir le nom de type correct, parcourez le module à l’aide de [Ildasm.exe (désassembleur IL)](ildasm-exe-il-disassembler.md). Vous pouvez également passer `*` en tant que paramètre de nom de module pour rechercher tous les modules managés chargés. Le paramètre *module name* peut également correspondre au nom du débogueur pour un module, comme `mscorlib` ou `image00400000`.<br /><br /> Cette commande prend en charge la syntaxe du débogueur Windows <`module`>`!`<`type`>. Le type doit être qualifié complet.|
|**Objsize** [ \<*Object address*> ] &#124; [**-Aggregate**] [**-Stat**]|Affiche la taille de l'objet spécifié. Si vous ne spécifiez aucun paramètre, la commande **ObjSize** affiche la taille de tous les objets trouvés dans les threads managés, ainsi que tous les handles du récupérateur de mémoire dans le processus et additionne la taille de tous les objets désignés par ces handles. La commande **ObjSize** inclut la taille de tous les objets enfants en plus du parent.<br /><br /> L’option **-aggregate** peut être utilisée avec l’argument **-stat** pour obtenir une vue détaillée des types qui sont encore associés à une racine. L’utilisation de **!dumpheap -stat** et **!objsize -aggregate -stat** vous permet de déterminer les objets qui ne sont plus associés à une racine et de diagnostiquer différents problèmes de mémoire.|
|**PrintException** [**-Nested**] [**-Lines**] [ \<*Exception object address*> ]<br /><br /> -ou-<br /><br /> **PE** [**-Nested**] [ \<*Exception object address*> ]|Affiche et met en forme les champs de tous les objets dérivés de la classe <xref:System.Exception> à l'adresse spécifiée. Si vous ne spécifiez pas d’adresse, la commande **PrintException** affiche la dernière exception levée dans le thread actuel.<br /><br /> L’option **-nested** affiche des détails sur les objets d’exception imbriquée.<br /><br /> L’option **-lines** affiche des informations sur la source, si elles sont disponibles.<br /><br /> Vous pouvez utiliser cette commande pour mettre en forme et consulter le champ `_stackTrace` qui est un tableau binaire.|
|**ProcInfo** [**-env**] [**-time**] [**-mem**]|Affiche les variables d'environnement pour le processus, le temps CPU noyau et les statistiques relatives à l'utilisation de la mémoire.|
|**RCWCleanupList**\<*RCWCleanupList address*>|Affiche la liste des wrappers RCW (Runtime Callable Wrapper) à l'adresse spécifiée qui sont en attente de nettoyage.|
|**SaveModule** \<*Base address*>\<*Filename*>|Écrit une image, chargée dans la mémoire à l'adresse spécifiée, dans le fichier spécifié.|
|**SOSFlush**|Vide un cache SOS interne.|
|**StopOnException** [**-Derived**] [**-Create** &#124; **-Create2**] \<*Exception*>\<*Pseudo-register number*>|Entraîne l'arrêt du débogueur lorsque l'exception spécifiée est levée, mais la poursuite de son exécution lorsque d'autres exceptions sont levées.<br /><br /> L’option **-derived** intercepte l’exception spécifiée et chaque exception dérivée de l’exception spécifiée.|
|**SyncBlk** [**-All** &#124; \<*syncblk number*> ]|Affiche la structure `SyncBlock` spécifiée ou l'ensemble des structures `SyncBlock`.  Si vous ne passez pas d’argument, la commande **SyncBlk** affiche la structure `SyncBlock` correspondant aux objets possédés par un thread.<br /><br /> Une structure `SyncBlock` est un conteneur pour les informations supplémentaires qui n'a pas besoin d'être créé pour chaque objet. Elle peut contenir des données COM Interop, des codes de hachage et des informations de verrouillage pour les opérations thread-safe.|
|**ThreadPool**|Affiche des informations sur le pool de threads managé, y compris le nombre de demandes de tâches dans la file d'attente, le nombre de threads de port de terminaison, et le nombre de minuteries.|
|**Token2EE** \<*module name*>\<*token*>|Convertit le jeton de métadonnées spécifié dans le module spécifié en structure `MethodTable` ou `MethodDesc`.<br /><br /> Vous pouvez passer `*` comme paramètre de nom de module pour rechercher le mappage de ce jeton dans chaque module managé chargé. Vous pouvez également passer le nom du débogueur pour un module, tel que `mscorlib` ou `image00400000`.|
|**Threads** [**-live**] [**-special**]|Affiche tous les threads managés dans le processus.<br /><br /> La commande **Threads** affiche l’ID abrégé du débogueur, l’ID de thread du CLR et l’ID de thread du système d’exploitation.  Par ailleurs, la commande **Threads** affiche une colonne Domain qui indique le domaine d’application dans lequel un thread s’exécute, une colonne APT qui affiche le mode COM cloisonné, et une colonne Exception qui affiche la dernière exception levée dans le thread.<br /><br /> L’option **-live** affiche les threads associés à un thread actif.<br /><br /> L’option **-special** affiche tous les threads spéciaux créés par le CLR. Les threads spéciaux incluent les threads du garbage collection (simultané et garbage collection du serveur), les threads d'assistance du débogueur, les threads finaliseurs, les threads Unload <xref:System.AppDomain> et les threads de minuterie Threadpool.|
|**ThreadState\<** *State value field* **>**|Affiche l'état du thread. Le paramètre `value` est la valeur du champ `State` dans la sortie du rapport **Threads**.<br /><br /> Exemple :<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [**-XML**]\<*filename*>|Écrit les informations du tas dans le fichier spécifié dans un format compris par le profileur du CLR. Quand l’option **-xml** est spécifiée, la commande **TraverseHeap** applique le format XML au fichier.<br /><br /> Vous pouvez télécharger le profileur CLR à partir du [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=67325).|
|**U** [**-gcinfo**] [**-ehinfo**] [**-n**] \<*MethodDesc address*> &#124;\<*Code address*>|Affiche un code machine annoté d'une méthode managée spécifié par un pointeur de structure `MethodDesc` pour la méthode ou par une adresse de code dans le corps de la méthode. La commande **U** affiche l’intégralité de la méthode du début à la fin, avec les annotations qui convertissent les jetons de métadonnées en noms.<br /><br /> L’option **-gcinfo** permet à la commande **U** d’afficher la structure `GCInfo` pour la méthode.<br /><br /> L’option **-ehinfo** affiche des informations sur les exceptions pour la méthode. Vous pouvez également obtenir ces informations avec la commande **EHInfo**.<br /><br /> L’option **-n** désactive l’affichage des noms de fichier source et des numéros de ligne. Si l'option SYMOPT_LOAD_LINES est spécifiée sur le débogueur, SOS recherche les symboles pour chaque frame managé et, s'il les trouve, affiche le nom de fichier source et le numéro de ligne correspondants. Vous pouvez spécifier l’option **-n** pour désactiver ce comportement.|
|**VerifyHeap**|Vérifie le tas de récupérateur de mémoire pour rechercher des signes d'altération et affiche toutes les erreurs trouvées.<br /><br /> Les altérations du tas peuvent être provoquées par des appels de code construits de manière incorrecte.|
|**VerifyObj**\<*object address*>|Vérifie l’objet passé comme argument à la recherche de signes d’altération.|
|**VMMap**|Parcourt l'espace d'adressage virtuel et affiche le type de protection appliqué à chaque région.|
|**VMStat**|Fournit un résumé de l’espace d’adressage virtuel, classé par type de protection appliqué à cette mémoire (libre, réservé, validé, privé, mappé, image). La colonne TOTAL affiche le résultat de la colonne MOYENNE multipliée par la colonne COMPTE BLQ.|

## <a name="remarks"></a>Remarques

L’extension de débogage SOS vous permet d’afficher des informations sur l’exécution du code au sein du CLR. Par exemple, vous pouvez utiliser l’extension de débogage SOS pour afficher des informations sur le tas managé, rechercher des altérations du tas, afficher les types de données internes utilisés par le runtime et afficher des informations sur l’ensemble du code managé exécuté au sein du runtime.

Pour utiliser l’extension de débogage SOS dans Visual Studio, installez le [Kit WDK (Windows Driver Kit)](/windows-hardware/drivers/download-the-wdk). Pour plus d’informations sur l’environnement de débogage intégré dans Visual Studio, consultez [Debugging Environments](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package) (Environnements de débogage).

Vous pouvez également utiliser l’extension de débogage SOS en la chargeant dans le [débogueur WinDbg.exe](/windows-hardware/drivers/debugger/debugger-download-tools) et en exécutant les commandes dans WinDbg.exe.

Pour charger l’Extension de débogage SOS dans le débogueur WinDbg.exe, exécutez la commande suivante dans l’outil :

```console
.loadby sos clr
```

WinDbg.exe et Visual Studio utilisent une version de SOS.dll qui correspond à la version de Mscorwks.dll actuellement utilisée. Par défaut, vous devez utiliser la version de SOS.dll qui correspond à la version actuelle de Mscorwks.dll.

Pour utiliser un fichier dump créé sur un autre ordinateur, vérifiez que le fichier Mscorwks.dll fourni avec cette installation se trouve dans votre chemin d'accès aux symboles, et chargez la version correspondante de SOS.dll.

Pour charger une version spécifique de SOS.dll, tapez la commande suivante dans le débogueur Windows :

```console
.load <full path to sos.dll>
```

## <a name="examples"></a>Exemples

La commande suivante affiche le contenu d'un tableau à l'adresse `00ad28d0`.  L'affichage démarre à partir du deuxième élément et se poursuit avec les cinq éléments suivants.

```console
!dumparray -start 2 -length 5 -detail 00ad28d0
```

La commande suivante affiche le contenu d'un assembly à l'adresse `1ca248`.

```console
!dumpassembly 1ca248
```

La commande suivante affiche des informations sur le tas de récupérateur de mémoire.

```console
!dumpheap
```

La commande suivante écrit le contenu du journal de contrainte en mémoire dans un fichier appelé StressLog.txt (par défaut) dans le répertoire actif.

```console
!DumpLog
```

La commande suivante affiche la structure `MethodDesc` à l'adresse `902f40`.

```console
!dumpmd 902f40
```

La commande suivante affiche des informations sur un module à l'adresse `1caa50`.

```console
!dumpmodule 1caa50
```

La commande suivante affiche des informations sur un objet à l'adresse `a79d40`.

```console
!DumpObj a79d40
```

La commande suivante affiche les champs d'une classe de valeur à l'adresse `00a79d9c`, à l'aide de la table de méthodes à l'adresse `0090320c`.

```console
!DumpVC 0090320c 00a79d9c
```

La commande suivante affiche la mémoire du processus utilisée par le récupérateur de mémoire.

```console
!eeheap -gc
```

La commande suivante affiche tous les objets planifiés pour la finalisation.

```console
!finalizequeue
```

La commande suivante détermine le domaine d'application d'un objet à l'adresse `00a79d98`.

```console
!findappdomain 00a79d98
```

La commande suivante affiche tous les handles du récupérateur de mémoire dans le processus actuel.

```console
!gcinfo 5b68dbb8
```

La commande suivante affiche les structures `MethodTable` et `EEClass` pour la méthode `Main`, dans la classe `MainClass`, dans le module `unittest.exe`.

```console
!name2ee unittest.exe MainClass.Main
```

La commande suivante affiche des informations sur le jeton de métadonnées à l'adresse `02000003` dans le module `unittest.exe`.

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
