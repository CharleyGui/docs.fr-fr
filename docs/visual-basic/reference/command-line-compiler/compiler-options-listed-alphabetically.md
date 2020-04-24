---
title: Options du compilateur classées par ordre alphabétique
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 85fb07f46c2d885491db7358f24b3b50836c2ca8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937759"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Visual Basic options du compilateur classées par ordre alphabétique
Le compilateur de ligne de commande Visual Basic est fourni comme alternative à la compilation de programmes à partir de l’environnement de développement intégré (IDE) de Visual Studio. La liste suivante répertorie les Visual Basic options du compilateur de ligne de commande triées par ordre alphabétique.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Option|Objectif|  
|------------|-------------|  
|[@ (spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Spécifie un fichier réponse.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Affiche les options du compilateur. Cette commande est identique à l'option `-help`. Aucune compilation n'a lieu.|  
|`-additionalfile`|Nomme des fichiers supplémentaires qui n'affectent pas directement la génération de code, mais peuvent être utilisés par des analyseurs pour produire des erreurs ou des avertissements.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.|  
|`-analyzer`|Exécute les analyseurs à partir de cet assembly (forme abrégée : -a).|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Spécifie l'adresse de base d'une DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Crée un fichier qui contient des informations qui facilitent le signalement d'un bogue.|  
|`-checksumalgorithm:<alg>`|Spécifiez l'algorithme de calcul de la somme de contrôle du fichier source stockée dans le fichier PDB.  Les valeurs prises en charge sont : SHA1 (par défaut) ou SHA256. <br>En raison de problèmes de collision avec SHA1, Microsoft recommande SHA256 ou une meilleure solution.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Génère des informations de débogage.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Définit des symboles de compilation conditionnelle.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Spécifie si l'assembly sera complètement ou partiellement signé.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Indique au compilateur de générer un assembly dont le contenu binaire est identique dans les compilations si les entrées sont identiques.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Traite les commentaires de documentation pour les diriger vers un fichier XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Spécifie comment le compilateur Visual Basic doit signaler les erreurs internes du compilateur.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Spécifie où les sections du fichier de sortie doivent être alignées.|  
|[-aide](../../../visual-basic/reference/command-line-compiler/help.md)|Affiche les options du compilateur. Cette commande est identique à l'option `-?`. Aucune compilation n'a lieu.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Indique si un fichier exécutable particulier prend en charge la fonctionnalité de randomisation du format d'espace d'adresse (ASLR) de forte entropie.|  
|[-importations](../../../visual-basic/reference/command-line-compiler/imports.md)|Importe un espace de noms à partir d'un assembly spécifié.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Spécifie un fichier qui contient une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Spécifiez la version de langue : 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md)|Spécifie l’emplacement des assemblys référencés par l’option [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) .|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Crée un lien à une ressource managée.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Spécifie la classe qui contient `Sub Main` la procédure à utiliser au démarrage.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Spécifie le nom de l'assembly dont un module fera partie.|  
|`-modulename:<string>`|Spécifiez le nom du module source.|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Définit le compilateur pour cibler le .NET Compact Framework.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Ne compilez pas avec Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Supprime les informations de bannière du compilateur.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Configure le compilateur pour ne pas référencer les bibliothèques standard.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Supprime la capacité du compilateur à générer des avertissements.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Active/désactive l'optimisation du code.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Spécifie si les comparaisons de chaînes doivent être binaires ou utiliser une sémantique spécifique aux paramètres régionaux.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Applique la déclaration explicite des variables.|  
|[-optioninfer (](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Applique une sémantique de langage stricte.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Spécifie un fichier de sortie.|  
|<code>-parallel[+&#124;-]</code>|Indique s'il faut utiliser la build simultanée (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Spécifie la plateforme de processeur ciblée par le compilateur pour le fichier de sortie.|  
|`-preferreduilang`|Spécifiez le nom de la langue de sortie préférée.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Recherche des fichiers sources à compiler dans les sous-répertoires.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importe des métadonnées à partir d'un assembly.|  
|[-refonly](refonly-compiler-option.md)|Génère uniquement un assembly de référence.|
|[-refout](refout-compiler-option.md)|Spécifie le chemin de sortie d’un assembly de référence.|
|[-removeintchecks (](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Désactive les contrôles de dépassement sur les entiers.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Incorpore une ressource managée dans un assembly.|  
|[-RootNamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Spécifie un espace de noms pour toutes les déclarations de type.|  
|`-ruleset:<file>`|Spécifiez un fichier ruleset qui désactive des diagnostics spécifiques.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Spécifie l'emplacement de Mscorlib.dll et de Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Spécifie la version minimale du sous-système utilisable par le fichier exécutable généré.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Spécifie le format du fichier de sortie.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Affiche les résultats de la compilation au format d'encodage UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Génère des informations supplémentaires lors de la compilation.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Transforme les avertissements en erreurs.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Insère un fichier .ico dans le fichier de sortie.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifie un fichier manifeste d'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable (PE) d'un projet.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Insère une ressource Win32 dans le fichier de sortie.|  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur Visual Basic par catégorie](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Gérer les propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
