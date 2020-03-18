---
title: Options du compilateur C# par catégorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972705"
---
# <a name="c-compiler-options-listed-by-category"></a>Options du compilateur C# par catégorie

Les options du compilateur suivantes sont triées par catégorie. Pour en obtenir la liste alphabétique, consultez [Options du compilateur C# par ordre alphabétique](listed-alphabetically.md).

## <a name="optimization"></a>Optimization

|Option|Objectif|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Spécifie la taille des sections dans le fichier de sortie.|
|[-optimiser](optimize-compiler-option.md)|Active/désactive les optimisations.|

## <a name="output-files"></a>Fichiers de sortie

|Option|Objectif|
|------------|-------------|
|[-déterministe](deterministic-compiler-option.md)|Indique au compilateur de générer un assembly dont le contenu binaire est identique dans les compilations si les entrées sont identiques.|
|[-doc](doc-compiler-option.md)|Spécifie un fichier XML dans lequel les commentaires de documentation traités doivent être écrits.|
|[-out](out-compiler-option.md)|Spécifie le fichier de sortie.|
|[-pathmap](pathmap-compiler-option.md)|Spécifie un mappage pour la sortie de noms de chemin d’accès source par le compilateur.|
|[-pdb](pdb-compiler-option.md)|Spécifie le nom et l'emplacement du fichier .pdb.|
|[-plateforme](platform-compiler-option.md)|Spécifie la plateforme de sortie.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Spécifie un langage pour les résultats de la compilation.|
|[-refout](refout-compiler-option.md)|Génère un assembly de référence en plus de l’assembly principal.|
|[-refonly](refonly-compiler-option.md)|Génère un assembly de référence au lieu d’un assembly principal.|
|[-cible](target-compiler-option.md)|Spécifie le format du fichier de sortie en utilisant l’une des cinq options suivantes : [-target:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md) ou [-target:winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<string>|Spécifiez le nom du module source.|

## <a name="net-framework-assemblies"></a>Assemblys .NET Framework

|Option|Objectif|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Spécifie un ou plusieurs modules à inclure dans cet assembly.|
|[-delaysign](delaysign-compiler-option.md)|Indique au compilateur d'ajouter la clé publique mais de laisser l'assembly non signé.|
|[-keycontainer](keycontainer-compiler-option.md)|Spécifie le nom du conteneur de la clé de chiffrement.|
|[-keyfile](keyfile-compiler-option.md)|Spécifie le nom du fichier contenant la clé de chiffrement.|
|[-lib](lib-compiler-option.md)|Spécifie l’emplacement des assemblys référencés par le biais de [-reference](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Indique au compilateur de ne pas importer la bibliothèque standard (mscorlib.dll).|
|[-publicign](publicsign-compiler-option.md)|Applique une clé publique sans signature de l’assembly, mais définit le bit dans l’assembly pour indiquer que l’assembly est signé.|
|[-référence](reference-compiler-option.md)|Importe des métadonnées à partir d'un fichier qui contient un assembly.|
|-analyzer|Exécutez les analyseurs à partir de cet assembly (forme abrégée : /a).|
|-additionalfile|Nomme des fichiers supplémentaires qui n'affectent pas directement la génération de code, mais peuvent être utilisés par des analyseurs pour produire des erreurs ou des avertissements.|
|-embed|Incorporer tous les fichiers sources du PDB.|
|-embed:\<file list>|Incorporer des fichiers spécifiques dans le PDB.|
## <a name="debuggingerror-checking"></a>Débogage/vérification des erreurs

|Option|Objectif|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Crée un fichier qui contient des informations qui facilitent le signalement d'un bogue.|
|[-vérifié](checked-compiler-option.md)|Indique si l'arithmétique sur les entiers qui dépasse les limites du type de données entraîne une exception au moment de l'exécution.|
|[-débog](debug-compiler-option.md)|Indique au compilateur d'émettre des informations de débogage.|
|[-erreurreport](errorreport-compiler-option.md)|Définit le comportement de signalement d'erreurs.|
|[-fullpaths](fullpaths-compiler-option.md)|Spécifie le chemin d'accès absolu au fichier de sortie du compilateur.|
|[-nowarn](nowarn-compiler-option.md)|Supprime la génération par le compilateur des avertissements spécifiés.|
|[-avertir](warn-compiler-option.md)|Définit le niveau d'avertissement.|
|[-warnaserror](warnaserror-compiler-option.md)|Transforme les avertissements en erreurs.|
|-ruleset:\<file>|Spécifiez un fichier ruleset qui désactive des diagnostics spécifiques.|

## <a name="preprocessor"></a>Préprocesseur

|Option|Objectif|
|------------|-------------|
|[-définir](define-compiler-option.md)|Définit les symboles du préprocesseur.|

## <a name="resources"></a>Ressources

|Option|Objectif|
|------------|-------------|
|[-lien](link-compiler-option.md)|Rend les informations de type COM dans les assemblys spécifiés disponibles pour le projet.|
|[-linkresource](linkresource-compiler-option.md)|Crée un lien à une ressource managée.|
|[-ressource](resource-compiler-option.md)|Incorpore une ressource .NET Framework dans le fichier de sortie.|
|[-win32icon](win32icon-compiler-option.md)|Spécifie un fichier .ico à insérer dans le fichier de sortie.|
|[-win32res](win32res-compiler-option.md)|Spécifie une ressource Win32 à insérer dans le fichier de sortie.|

## <a name="miscellaneous"></a>Divers

|Option|Objectif|
|------------|-------------|
|[@](response-file-compiler-option.md)|Spécifie un fichier réponse.|
|[-?](help-compiler-option.md)|Répertorie les options du compilateur dans stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Spécifie l'adresse de base préférée à laquelle charger une DLL.|
|[-page de code](codepage-compiler-option.md)|Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.|
|[-aide](help-compiler-option.md)|Répertorie les options du compilateur dans stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Spécifie que le fichier exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR).|
|[-langversion](langversion-compiler-option.md)|Spécifie la version de langage : Default, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 ou Latest |
|[-principal](main-compiler-option.md)|Spécifie l’emplacement de la méthode **Main**.|
|[-noconfig](noconfig-compiler-option.md)|Indique au compilateur ne pas compiler avec csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Supprime les informations de bannière du compilateur.|
|[-reurse](recurse-compiler-option.md)|Recherche des fichiers sources à compiler dans les sous-répertoires.|
|[-subsystèmesversion](subsystemversion-compiler-option.md)|Spécifie la version minimale du sous-système utilisable par le fichier exécutable.|
|[-dangereux](unsafe-compiler-option.md)|Active la compilation du code qui utilise le mot clé [unsafe](../keywords/unsafe.md).|
|[-utf8output](utf8output-compiler-option.md)|Affiche les résultats de la compilation au format d'encodage UTF-8.|
|-parallel[+&#124;-]|Indique s'il faut utiliser la build simultanée (+).|
|-checksumalgorithm:\<alg>|Spécifiez l'algorithme de calcul de la somme de contrôle du fichier source stockée dans le fichier PDB.  Les valeurs prises en charge sont : SHA1 (par défaut) ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|

## <a name="obsolete-options"></a>Options obsolètes

|Option|Objectif|
|---|---|
|-incremental|Active la compilation incrémentielle.|

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](index.md)
- [Options du compilateur C# par ordre alphabétique](listed-alphabetically.md)
- [Comment définir les variables de l’environnement pour la ligne de commandement visual studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
