---
title: MDbg.exe (débogueur de ligne de commande du .NET Framework)
description: Comprenez MDbg.exe, le débogueur de ligne de commande pour .NET, qui aide les fournisseurs d’outils et les développeurs d’applications à trouver et à résoudre les bogues dans les programmes ciblant le CLR.
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
ms.openlocfilehash: 8953db973e231014284ec6585012edc7f3ea11f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279166"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (débogueur de ligne de commande du .NET Framework)

Le débogueur de ligne de commande du .NET Framework aide les fournisseurs d'outils et les développeurs d'applications à trouver et à corriger les bogues dans les programmes qui ont pour cible le Common Language Runtime du .NET Framework. Cet outil utilise l'API de débogage du runtime pour fournir des services de débogage. Vous pouvez utiliser MDbg.exe pour déboguer uniquement du code managé ; il n'y a pas de prise en charge du débogage du code non managé.  
  
Cet outil est disponible via NuGet. Pour plus d’informations sur l’installation, consultez [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Pour exécuter l'outil, utilisez la console du Gestionnaire de package. Pour plus d’informations sur la manière d’utiliser la console du Gestionnaire de package, consultez l’article [Console du Gestionnaire de package](/nuget/tools/package-manager-console).
  
À l'invite du Gestionnaire de package, tapez ce qui suit :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Commandes  

 Quand vous êtes dans le débogueur (comme indiqué par l’invite **mdbg>**), tapez l’une des commandes décrites dans la section suivante :  
  
 **commande** [*arguments*]  
  
 Les commandes de MDbg.exe respectent la casse.  
  
|Commande|Description|  
|-------------|-----------------|  
|**ap**[**rocess**] [*number*]|Passe à un autre processus débogué ou imprime les processus disponibles. Les numéros ne sont pas de véritables ID de processus (PIDs), mais une liste indexée de 0.|  
|**a**[**ttach**] [*pid*]|Est joint à un processus ou imprime les processus disponibles.|  
|**b**[**reak**] [*ClassName.Method* &#124; *FileName:LineNo*]|Définit un point d'arrêt sur la méthode spécifiée. Les modules sont numérisés séquentiellement.<br /><br /> -   **break** *FileName:LineNo* définit un point d’arrêt à un emplacement dans la source.<br />-   **break** *~number* définit un point d’arrêt sur un symbole affiché récemment avec la commande **x**.<br />-   **break** *module!ClassName.Method+IlOffset* définit un point d’arrêt sur l’emplacement complet.|  
|**block**[**ingObjects**]|Affiche les verrous du moniteur, qui sont des threads bloquants.|  
|**ca**[**tch**] [*exceptionType*]|Provoque l'arrêt du débogueur à chaque exception, pas uniquement sur les exceptions non gérées.|  
|**cl**[**earException**]|Marque l'exception actuelle comme gérée afin que l'exécution puisse continuer. Si la cause de l'exception n'a pas été traitée, l'exception peut être rapidement levée une nouvelle fois.|  
|**conf**[**ig**] [*option value*]|Affiche toutes les options configurables et indique comment les options sont appelées sans aucune valeur facultative. Si l'option est spécifiée, définit `value` comme l'option actuelle. Les options actuellement disponibles sont les suivantes :<br /><br /> -   `extpath` définit le chemin pour rechercher des extensions quand la commande `load` est utilisée.<br />-   `extpath+` ajoute un chemin pour le chargement des extensions.|  
|**del**[**ete**]|Supprime un point d'arrêt.|  
|**de**[**tacher la**]|Se détache d'un processus débogué.|  
|**d**[**own**] [*frames*]|Déplace le frame de pile actif vers le bas.|  
|**echo**|Répercute un message dans la console.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Active (1) ou désactive (0) des notifications personnalisées pour le type spécifié.|  
|**ex**[**it**] [*exitcode*]|Quitte l'interpréteur de commandes MDbg.exe et spécifie éventuellement le code de sortie du processus.|  
|**fo**[**reach**] [*OtherCommand*]|Exécute une commande sur tous les threads. *OtherCommand* est une commande valide qui fonctionne sur un thread ; **foreach** *OtherCommand* exécute la même commande sur tous les threads.|  
|**f**[**unceval**] [ `-ad` *num*] *nomfonction* [*args...* ]|Exécute une évaluation de fonction sur le thread actif actuel où la fonction à évaluer est *functionName*. Le nom de fonction doit être pleinement qualifié, espaces de noms compris.<br /><br /> L'option `-ad` spécifie le domaine d'application à utiliser pour résoudre la fonction. Si l'option `-ad` n'est pas spécifiée, le domaine d'application pour la résolution est par défaut le domaine d'application où se trouve le thread qui est utilisé pour l'évaluation de la fonction.<br /><br /> Si la fonction qui est évaluée n'est pas statique, le premier paramètre passé doit être un pointeur `this`. Les arguments de l'évaluation de fonction sont recherchés dans tous les domaines d'application.<br /><br /> Pour demander une valeur d'un domaine d'application, préfixez la variable avec le module et le nom du domaine d'application, par exemple `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. Cette commande évalue la fonction `System.Object.ToString` dans le domaine d'application `0`. Étant donné que la méthode `ToString` est une fonction d'instance, le premier paramètre doit être un pointeur `this`.|  
|**g**[**o**]|Avec cette commande, le programme continue jusqu'à ce qu'il rencontre un point d'arrêt, que le programme se termine ou qu'un événement (par exemple, une exception non gérée) provoque l'arrêt du programme.|  
|**h**[**IDE**] [*commande*]<br /><br /> -ou-<br /><br /> **?** [*commande*]|Affiche une description de toutes les commandes ou une description détaillée d'une commande spécifiée.|  
|**ig**[**nore**] [*event*]|Entraîne l'arrêt du débogueur uniquement sur les exceptions non gérées.|  
|**int**[**ercept**] *FrameNumber*|Restaure le débogueur à un numéro de frame spécifié.<br /><br /> Si le débogueur rencontre une exception, utilisez cette commande pour restaurer le débogueur au numéro de frame spécifié. Vous pouvez modifier l’état du programme à l’aide de la commande **set** et continuer à utiliser la commande **go**.|  
|**k**[**malade**]|Arrête le processus actif.|  
|**l**[**ist**] [*modules* &#124; *appdomains* &#124; *assemblies*]|Affiche les modules, domaines d'application ou assemblys chargés.|  
|**lo**[**ad**] *assemblyName*|Charge une extension de la manière suivante : l'assembly spécifié est chargé et une tentative est ensuite faite pour exécuter la méthode statique `LoadExtension` à partir du type `Microsoft.Tools.Mdbg.Extension.Extension`.|  
|**log** [*eventType*]|Définir ou afficher les événements à enregistrer.|  
|**mo**[**de**] [*option on/off*]|Définit différentes options du débogueur. Utilisez `mode` sans option pour obtenir la liste des modes de débogage et leurs paramètres actuels.|  
|**mon**[**itorInfo**] *monitorReference*|Affiche les informations de verrou du moniteur d'objet.|  
|**newo**[**bj**] *typeName* [*arguments...*]|Crée un objet de type *typeName*.|  
|**n**[**ext**]|Exécute le code et passe à la ligne suivante (même si la ligne suivante contient de nombreux appels de fonction).|  
|**Opendump** *pathToDumpFile*|Ouvre le fichier dump spécifié pour le débogage.|  
|**o**[**ut**]|Déplace le curseur à la fin de la fonction actuelle.|  
|**pa**[**th**] [*pathName*]|Recherche dans le chemin d’accès spécifié les fichiers sources si l’emplacement dans les binaires n’est pas disponible.|  
|**p**[**rint**] [*var*] &#124; [`-d`]|Imprime toutes les variables dans la portée (**print**), imprime la variable spécifiée (**print** *var*) ou imprime les variables du débogueur (**print**`-d`).|  
|**printe**[**xception**] [*-r*]|Imprime la dernière exception sur le thread actuel. Utilisez l'option `–r` (récursive) pour parcourir la propriété `InnerException` sur l'objet exception pour obtenir des informations sur la chaîne entière des exceptions.|  
|**pro**[**cessenum**]|Affiche les processus actifs.|  
|**q**[**uit**] [*exitcode*]|Quitte l'interpréteur de commandes MDbg.exe, en spécifiant éventuellement le code de sortie du processus.|  
|**re**[**sume**] [`*` &#124; [`~`]*threadNumber*]|Reprend le thread actuel ou le thread spécifié par le paramètre *threadNumber*.<br /><br /> Si le paramètre *threadNumber* est spécifié comme `*` ou si le numéro de thread commence par `~`, la commande s’applique à tous les threads à l’exception de celui spécifié par *threadNumber*.<br /><br /> Reprendre un thread non suspendu n'a aucun effet.|  
|**r**[**un**] [ `-d` ( `ebug` ) &#124;- `o` ( `ptimize` ) &#124;`-enc` ] [[*path_to_exe*] [*args_to_exe*]]|Arrête le processus en cours (le cas échéant) et en démarre un nouveau. Si aucun argument exécutable n'est passé, cette commande exécute le programme qui était précédemment exécuté avec la commande `run`. Si l'argument exécutable est fourni, le programme spécifié est exécuté à l'aide des arguments éventuellement fournis.<br /><br /> Si les événements de chargement de classe, de chargement de module et de démarrage de thread sont ignorés (comme c'est le cas par défaut), le programme s'arrête sur la première instruction exécutable du thread principal.<br /><br /> Vous pouvez forcer le débogueur à effectuer une compilation juste-à-temps (JIT) du code à l'aide de l'une des trois balises suivantes :<br /><br /> -   `-d`*(* `ebug` *)* désactive les optimisations. Il s'agit de la valeur par défaut pour MDbg.exe.<br />-   `-o`*(* `ptimize` *)* force le code à s’exécuter de la même façon qu’en dehors du débogueur, mais rend également l’expérience de débogage plus difficile. Ceci est la valeur par défaut pour une utilisation en dehors du débogueur.<br />-   `-enc` active la fonction Modifier et continuer, mais entraîne une baisse des performances.|  
|**Set** *variable*=*value*|Change la valeur de n'importe quelle variable à l'intérieur de la portée.<br /><br /> Vous pouvez également créer vos propres variables de débogueur et leur assigner des valeurs de référence à partir de votre application. Ces valeurs agissent comme des handles pour la valeur d'origine, même la valeur d'origine est hors de portée. Toutes les variables du débogueur doivent commencer par `$` (par exemple, `$var`). Effacez ces handles en leur donnant une valeur nulle à l'aide de la commande suivante :<br /><br /> `set $var=`|  
|**SetIP** [ `-il` ] *nombre*|Définit le pointeur d'instruction (IP) actuel dans le fichier à la position spécifiée. Si vous spécifiez l'option `-il`, le numéro représente un décalage MSIL (Microsoft intermediate langage) dans la méthode. Autrement, le nombre représente un numéro de ligne source.|  
|**sh**[**ow**] [*lines*]|Spécifie le nombre de lignes à afficher.|  
|**s**[**tape**]|Déplace l'exécution à la fonction suivante sur la ligne en cours, ou passe à la ligne suivante en l'absence de fonction dans laquelle passer.|  
|**su**[**spend**] [\* &#124; [~]*threadNumber*]|Suspend le thread actuel ou le thread spécifié par le paramètre *threadNumber*.  Si *threadNumber* est spécifié comme `*`, la commande s’applique à tous les threads. Si le numéro de thread commence par `~`, la commande s’applique à tous les threads à l’exception de celui spécifié par *threadNumber*. Les threads suspendus sont exclus de l’exécution quand le processus est exécuté par la commande **go** ou **step**. S’il n’existe aucun thread non suspendu dans le processus et que vous émettez la commande **go**, le processus ne continuera pas. Dans ce cas, appuyez sur Ctrl+C pour entrer dans le processus.|  
|**sy**[**mbol**] *commandName* [*commandValue*]|Spécifie l'une des commandes suivantes :<br /><br /> -   `symbol path` [`"value"`] - Affiche ou définit le chemin actuel des symboles.<br />-   `symbol addpath``"value"`-S’ajoute à votre chemin d’accès aux symboles en cours.<br />-   `symbol reload` [`"module"`] - Recharge soit tous les symboles, soit les symboles du module spécifié.<br />-   `symbol list` [`module`] - Affiche les symboles actuellement chargés soit pour tous les modules, soit pour le module spécifié.|  
|**t**[**hread**] [*newThread*] [-*Nick surnom*`]`|La commande de threads sans paramètre affiche tous les threads managés dans le processus en cours. Les threads sont généralement identifiés par leur numéro de thread. Toutefois, si le thread a un surnom assigné, celui-ci est affiché à la place. Vous pouvez utiliser le paramètre `-nick` pour assigner un surnom à un thread.<br /><br /> -   **thread** `-nick` *threadName* assigne un surnom au thread en cours d’exécution.<br /><br /> Les surnoms ne peuvent pas être des nombres. Si le thread actuel a déjà un surnom assigné, le nouveau vient remplacer l'ancien. Si le nouveau surnom est une chaîne vide (""), le surnom du thread en cours est supprimé et aucun nouveau surnom n'est assigné au thread.|  
|**u**[**p**]|Déplace le frame de la pile vers le haut.|  
|**uwgc**[**handle**] [*var*] &#124; [*address*]|Imprime la variable suivie par un handle. Le handle peut être spécifié par un nom ou par une adresse.|  
|**when**|Affiche les instructions `when` actuellement actives.<br /><br /> **lorsque** **Delete All** &#124; `num` [ `num` [ `num` ...]]-supprime l' `when` instruction spécifiée par le nombre, ou toutes les `when` instructions si `all` est spécifié.<br /><br /> **quand** `stopReason` [ `specific_condition` ] **ne** `cmd` [ `cmd` [ `cmd` ...]]-Le paramètre *stopReason* peut avoir l’une des valeurs suivantes :<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* peut avoir l’une des valeurs suivantes :<br /><br /> -   *number* - Pour `ThreadCreated` et `BreakpointHit`, déclenche l’action uniquement quand elle est arrêtée par un numéro d’ID/de point d’arrêt de thread de même valeur.<br />-[ `!` ]*nom* -pour `ModuleLoaded` , `ClassLoaded` , `AssemblyLoaded` , `AssemblyUnloaded` , `ExceptionThrown` et `UnhandledExceptionThrown` , déclenche l’action uniquement lorsque le nom correspond au nom du *stopReason*.<br /><br /> *specific_condition* doit être vide pour d’autres valeurs de *stopReason*.|  
|**w**[**ici**] [ `-v` ] [ `-c` *profondeur*] [*threadID*]|Affiche des informations de débogage sur des frames de pile.<br /><br /> -   L’option `-v` fournit des informations détaillées sur chacun des frames de pile affichés.<br />-   La spécification d’un nombre pour `depth` limite le nombre de frames affichés. Utilisez la commande **all** pour afficher tous les frames. La valeur par défaut est 100.<br />-   Si vous spécifiez le paramètre *threadID*, vous pouvez contrôler le thread qui est associé à la pile. La valeur par défaut est le thread actuel uniquement. Utilisez la commande **all** pour obtenir tous les threads.|  
|**x** [ `-c` *numSymbols*] [*module*[ `!` *pattern*]]|Affiche les fonctions qui correspondent à `pattern` pour un module.<br /><br /> Si *numSymbols* est spécifié, la sortie est limitée au nombre spécifié. Si `!` (indiquant une expression régulière) n’est pas spécifié pour *pattern*, toutes les fonctions sont affichées. Si *module* n’est pas fourni, tous les modules chargés sont affichés. Les symboles ( *~#* ) peuvent être utilisés pour définir des points d’arrêt à l’aide de la commande **break** .|  
  
## <a name="remarks"></a>Notes  

 Compilez l'application à déboguer à l'aide d'indicateurs spécifiques au compilateur, ce qui oblige ce dernier à générer des symboles de débogage. Pour plus d'informations sur ces indicateurs, consultez la documentation de votre compilateur. Il est toujours possible de déboguer des applications optimisées, mais il manquera certaines informations de débogage. Par exemple, un grand nombre de variables locales ne seront pas visibles et certaines lignes sources seront incorrectes.  
  
 Après avoir compilé votre application, tapez **mdbg** à l’invite de commandes pour démarrer une session de débogage, comme le montre l’exemple suivant.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 L'invite `mdbg>` indique que vous vous trouvez dans le débogueur.  
  
 Une fois que vous êtes dans le débogueur, utilisez les commandes et les arguments décrits dans la section précédente.  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
