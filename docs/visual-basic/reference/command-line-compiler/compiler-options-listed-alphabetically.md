---
title: Options du compilateur classées par ordre alphabétique
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: d0dbe785edf7a9aa029d4be08a9b854cf1fb2b79
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085293"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Visual Basic options du compilateur classées par ordre alphabétique

Le compilateur de ligne de commande Visual Basic est fourni comme alternative à la compilation de programmes à partir de l’environnement de développement intégré (IDE) de Visual Studio. La liste suivante répertorie les Visual Basic options du compilateur de ligne de commande triées par ordre alphabétique.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Option|Objectif|  
|------------|-------------|  
|[@ (spécifier un fichier réponse)](specify-response-file.md)|Spécifie un fichier réponse.|  
|[-?](help.md)|Affiche les options du compilateur. Cette commande est identique à l'option `-help`. Aucune compilation n'a lieu.|  
|`-additionalfile`|Nomme des fichiers supplémentaires qui n'affectent pas directement la génération de code, mais peuvent être utilisés par des analyseurs pour produire des erreurs ou des avertissements.|  
|[-addmodule](addmodule.md)|Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.|  
|`-analyzer`|Exécute les analyseurs à partir de cet assembly (forme abrégée : -a).|  
|[-baseaddress](baseaddress.md)|Spécifie l'adresse de base d'une DLL.|  
|[-bugreport](bugreport.md)|Crée un fichier qui contient des informations qui facilitent le signalement d'un bogue.|  
|`-checksumalgorithm:<alg>`|Spécifiez l'algorithme de calcul de la somme de contrôle du fichier source stockée dans le fichier PDB.  Les valeurs prises en charge sont : SHA1 (par défaut) ou SHA256. <br>En raison de problèmes de collision avec SHA1, Microsoft recommande SHA256 ou une meilleure solution.|  
|[-CodePage](codepage.md)|Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.|  
|[-débogage](debug.md)|Génère des informations de débogage.|  
|[-définir](define.md)|Définit des symboles de compilation conditionnelle.|  
|[-delaysign](delaysign.md)|Spécifie si l'assembly sera complètement ou partiellement signé.|  
|[-déterministe](deterministic.md)|Indique au compilateur de générer un assembly dont le contenu binaire est identique dans les compilations si les entrées sont identiques.|
|[-doc](doc.md)|Traite les commentaires de documentation pour les diriger vers un fichier XML.|  
|[-errorreport](errorreport.md)|Spécifie comment le compilateur Visual Basic doit signaler les erreurs internes du compilateur.|  
|[-filealign](filealign.md)|Spécifie où les sections du fichier de sortie doivent être alignées.|  
|[-aide](help.md)|Affiche les options du compilateur. Cette commande est identique à l'option `-?`. Aucune compilation n'a lieu.|  
|[-highentropyva](highentropyva.md)|Indique si un fichier exécutable particulier prend en charge la fonctionnalité de randomisation du format d'espace d'adresse (ASLR) de forte entropie.|  
|[-imports](imports.md)|Importe un espace de noms à partir d'un assembly spécifié.|  
|[-keycontainer](keycontainer.md)|Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.|  
|[-keyfile](keyfile.md)|Spécifie un fichier qui contient une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.|  
|[-langversion](langversion.md)|Spécifiez la version de langue : 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-libpath](libpath.md)|Spécifie l’emplacement des assemblys référencés par l’option [-Reference](reference.md) .|  
|[-linkresource](linkresource.md)|Crée un lien à une ressource managée.|  
|[-main](main.md)|Spécifie la classe qui contient la `Sub Main` procédure à utiliser au démarrage.|  
|[-moduleassemblyname](moduleassemblyname.md)|Spécifie le nom de l'assembly dont un module fera partie.|  
|`-modulename:<string>`|Spécifiez le nom du module source.|  
|[-netcf](netcf.md)|Définit le compilateur pour cibler le .NET Compact Framework.|  
|[-noconfig](noconfig.md)|Ne compilez pas avec Vbc.rsp.|  
|[-nologo](nologo.md)|Supprime les informations de bannière du compilateur.|  
|[-nostdlib](nostdlib.md)|Configure le compilateur pour ne pas référencer les bibliothèques standard.|  
|[-nowarn](nowarn.md)|Supprime la capacité du compilateur à générer des avertissements.|  
|[-nowin32manifest](nowin32manifest.md)|Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.|  
|[-optimiser](optimize.md)|Active/désactive l'optimisation du code.|  
|[-optioncompare](optioncompare.md)|Spécifie si les comparaisons de chaînes doivent être binaires ou utiliser une sémantique spécifique aux paramètres régionaux.|  
|[-optionexplicit](optionexplicit.md)|Applique la déclaration explicite des variables.|  
|[-optioninfer](optioninfer.md)|Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.|  
|[-optionstrict](optionstrict.md)|Applique une sémantique de langage stricte.|  
|[-out](out.md)|Spécifie un fichier de sortie.|  
|<code>-parallel[+&#124;-]</code>|Indique s'il faut utiliser la build simultanée (+).|  
|[-plateforme](platform.md)|Spécifie la plateforme de processeur ciblée par le compilateur pour le fichier de sortie.|  
|`-preferreduilang`|Spécifiez le nom de la langue de sortie préférée.|  
|[-quiet](quiet.md)|Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.|  
|[-recurse](recurse.md)|Recherche des fichiers sources à compiler dans les sous-répertoires.|  
|[-Référence](reference.md)|Importe des métadonnées à partir d'un assembly.|  
|[-refonly](refonly-compiler-option.md)|Génère uniquement un assembly de référence.|
|[-refout](refout-compiler-option.md)|Spécifie le chemin de sortie d’un assembly de référence.|
|[-removeintchecks](removeintchecks.md)|Désactive les contrôles de dépassement sur les entiers.|  
|[-ressource](resource.md)|Incorpore une ressource managée dans un assembly.|  
|[-rootnamespace](rootnamespace.md)|Spécifie un espace de noms pour toutes les déclarations de type.|  
|`-ruleset:<file>`|Spécifiez un fichier ruleset qui désactive des diagnostics spécifiques.|  
|[-sdkpath](sdkpath.md)|Spécifie l'emplacement de Mscorlib.dll et de Microsoft.VisualBasic.dll.|  
|[-subsystemversion](subsystemversion.md)|Spécifie la version minimale du sous-système utilisable par le fichier exécutable généré.|  
|[-cible](target.md)|Spécifie le format du fichier de sortie.|  
|[-utf8output](utf8output.md)|Affiche les résultats de la compilation au format d'encodage UTF-8.|  
|[-vbruntime](vbruntime.md)|Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.|  
|[-verbose](verbose.md)|Génère des informations supplémentaires lors de la compilation.|  
|[-warnaserror](warnaserror.md)|Transforme les avertissements en erreurs.|  
|[-win32icon](win32icon.md)|Insère un fichier .ico dans le fichier de sortie.|  
|[-win32manifest](win32manifest.md)|Identifie un fichier manifeste d'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable (PE) d'un projet.|  
|[-win32resource](win32resource.md)|Insère une ressource Win32 dans le fichier de sortie.|  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur Visual Basic par catégorie](compiler-options-listed-by-category.md)
- [Gérer les propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
