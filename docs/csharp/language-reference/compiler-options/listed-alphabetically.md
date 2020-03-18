---
title: Options du compilateur C# par ordre alphabétique
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: d6d471cd27f35de6325a130e6c909d13cb1dcc85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972742"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Options du compilateur C# par ordre alphabétique

Les options du compilateur suivantes sont triées par ordre alphabétique. Pour obtenir la liste par catégorie, consultez [Options du compilateur C# par catégorie](listed-by-category.md).

|Option|Objectif|
|------------|-------------|
|[@](response-file-compiler-option.md)|Lit un fichier réponse pour obtenir plus d'options.|
|[-?](help-compiler-option.md)|Affiche un message d'utilisation dans stdout.|
|-additionalfile|Nomme des fichiers supplémentaires qui n'affectent pas directement la génération de code, mais peuvent être utilisés par des analyseurs pour produire des erreurs ou des avertissements.|
|[-addmodule](addmodule-compiler-option.md)|Lie les modules spécifiés dans cet assembly.|
|-analyzer|Exécute les analyseurs à partir de cet assembly (forme abrégée : -a).|
|[-appconfig](appconfig-compiler-option.md)|Spécifie l’emplacement du fichier app.config au moment de la liaison d’assembly.|
|[-baseaddress](baseaddress-compiler-option.md)|Spécifie l'adresse de base de la bibliothèque à générer.|
|[-bugreport](bugreport-compiler-option.md)|Crée un fichier de rapport de bogue. Ce fichier est envoyé avec les informations d’incident s’il est utilisé avec -errorprompt:prompt ou -errorreport:send.|
|[-vérifié](checked-compiler-option.md)|Indique au compilateur de générer des contrôles de dépassement de capacité.|
|-checksumalgorithm:\<alg>|Spécifie l'algorithme de calcul de la somme de contrôle du fichier source stockée dans le fichier PDB.  Les valeurs prises en charge sont : SHA256 (par défaut) ou SHA1.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256. |
|[-page de code](codepage-compiler-option.md)|Spécifie la page de codes à utiliser à l'ouverture des fichiers sources.|
|[-débog](debug-compiler-option.md)|Émet des informations de débogage.|
|[-définir](define-compiler-option.md)|Définit des symboles de compilation conditionnelle.|
|[-delaysign](delaysign-compiler-option.md)|Diffère la signature de l'assembly en utilisant uniquement la partie publique de la clé de nom fort.|
|[-déterministe](deterministic-compiler-option.md)|Indique au compilateur de générer un assembly dont le contenu binaire est identique dans les compilations si les entrées sont identiques.|
|[-doc](doc-compiler-option.md)|Spécifie un fichier de documentation XML à générer.|
|-embed|Incorporer tous les fichiers sources du PDB.|
|-embed:\<file list>|Incorporer des fichiers spécifiques dans le PDB.|
|-errorendlocation|Ligne et colonne de sortie de l'emplacement de fin de chaque erreur.|
|-errorlog:\<file>|Spécifier un fichier pour journaliser tous les diagnostics du compilateur et de l’analyseur.|
|[-erreurreport](errorreport-compiler-option.md)|Spécifie comment gérer les erreurs internes du compilateur : invite, envoi et aucune gestion. La valeur par défaut est aucune gestion.|
|[-filealign](filealign-compiler-option.md)|Spécifie l'alignement utilisé pour les sections du fichier de sortie.|
|[-fullpaths](fullpaths-compiler-option.md)|Indique au compilateur de générer des chemins d’accès complets.|
|[-aide](help-compiler-option.md)|Affiche un message d'utilisation dans stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Spécifie que la randomisation du format d'espace d'adresse (ASLR) d'entropie élevée est prise en charge.|
|-incremental|Active la compilation incrémentielle [obsolète].|
|[-keycontainer](keycontainer-compiler-option.md)|Spécifie un conteneur de clé de nom fort.|
|[-keyfile](keyfile-compiler-option.md)|Spécifie un fichier de clé de nom fort.|
|[-langversion:\<string>](langversion-compiler-option.md)|Spécifie la version de langage : Default, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 ou Latest |
|[-lib](lib-compiler-option.md)|Spécifie les répertoires supplémentaires dans lesquels rechercher des références.|
|[-lien](link-compiler-option.md)|Rend les informations de type COM dans les assemblys spécifiés disponibles pour le projet.|
|[-linkresource](linkresource-compiler-option.md)|Lie la ressource spécifiée à cet assembly.|
|[-principal](main-compiler-option.md)|Spécifie le type qui contient le point d'entrée (ignorez tous les autres points d'entrée possibles)|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Spécifie un assembly dont les types non publics sont accessibles par un .netmodule.|
|-modulename:\<string>|Spécifiez le nom du module source.|
|[-noconfig](noconfig-compiler-option.md)|Indique au compilateur ne pas inclure automatiquement de fichier CSC.RSP.|
|[-nologo](nologo-compiler-option.md)|Supprime le message de copyright du compilateur.|
|[-nostdlib](nostdlib-compiler-option.md)|Indique au compilateur de ne pas référencer la bibliothèque standard (mscorlib.dll).|
|[-nowarn](nowarn-compiler-option.md)|Désactive des messages d'avertissement spécifiques.|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Indique au compilateur de ne pas incorporer un manifeste d'application dans le fichier exécutable.|
|[-optimiser](optimize-compiler-option.md)|Active/désactive les optimisations.|
|[-out](out-compiler-option.md)|Spécifie le nom de fichier de sortie (par défaut : nom de base du fichier avec classe principale ou premier fichier).|
|-parallel[+&#124;-]|Indique s'il faut utiliser la build simultanée (+).|
|[-pathmap](pathmap-compiler-option.md)|Spécifie un mappage pour la sortie de noms de chemin d’accès source par le compilateur.|
|[-pdb](pdb-compiler-option.md)|Spécifie le nom et l'emplacement du fichier .pdb.|
|[-plateforme](platform-compiler-option.md)|Limite les plateformes sur lesquelles ce code peut s'exécuter : x86, Itanium, x64, anycpu ou anycpu32bitpreferred. La valeur par défaut est anycpu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Spécifie la langue à utiliser pour la sortie du compilateur.|
|[-publicign](publicsign-compiler-option.md)|Applique une clé publique sans signature de l’assembly, mais définit le bit dans l’assembly pour indiquer que l’assembly est signé.|
|[-reurse](recurse-compiler-option.md)|Inclut tous les fichiers dans le répertoire et les sous-répertoires actuels en fonction des spécifications de caractères génériques.|
|[-référence](reference-compiler-option.md)|Référence les métadonnées à partir des fichiers d'assembly spécifiés.|
|[-refout](refout-compiler-option.md)|Génère un assembly de référence en plus de l’assembly principal.|
|[-refonly](refonly-compiler-option.md)|Génère un assembly de référence au lieu d’un assembly principal.|
|-reportanalyzer|Créer un rapport sur les informations supplémentaires de l’analyseur, comme l’heure d’exécution.|
|[-ressource](resource-compiler-option.md)|Incorpore la ressource spécifiée.|
|-ruleset:\<file>|Spécifiez un fichier ruleset qui désactive des diagnostics spécifiques.|
|[-subsystèmesversion](subsystemversion-compiler-option.md)|Spécifie la version minimale du sous-système utilisable par le fichier exécutable.|
|[-cible](target-compiler-option.md)|Specifie le format du fichier de sortie en utilisant l’une des quatre options: [-cible:appcontainerexe](target-appcontainerexe-compiler-option.md), [-cible:exe](target-exe-compiler-option.md), [-cible:bibliothèque](target-library-compiler-option.md), [-cible:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md), [-target:winmdobj](target-winmdobj-compiler-option.md).|
|[-dangereux](unsafe-compiler-option.md)|Autorise le code [unsafe](../keywords/unsafe.md).|
|[-utf8output](utf8output-compiler-option.md)|Génère des messages du compilateur encodés en UTF-8.|
|-version|Afficher le numéro de version du compilateur et quitter.|
|[-avertir](warn-compiler-option.md)|Définit le niveau d'avertissement (entre 0 et 4).|
|[-warnaserror](warnaserror-compiler-option.md)|Signale des avertissements spécifiques en tant qu'erreurs.|
|[-win32icon](win32icon-compiler-option.md)|Utilise cette icône pour la sortie.|
|[-win32manifest](win32manifest-compiler-option.md)|Spécifie un fichier manifeste win32 personnalisé.|
|[-win32res](win32res-compiler-option.md)|Spécifie le fichier de ressources win32 (.res).|

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](index.md)
- [Options du compilateur C# par catégorie](listed-by-category.md)
- [Comment définir les variables de l’environnement pour la ligne de commandement visual studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<compilateur> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
