---
title: Resgen.exe (Resource File Generator)
ms.date: 03/30/2017
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
ms.openlocfilehash: b9be030689ecf78b3482743e486e32012e9ca5d4
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201103"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Resource File Generator)
Le Générateur de fichiers de ressources (Resgen.exe) convertit les fichiers texte (.txt ou .restext) et les fichiers de format de ressource XML (.resx) en fichiers binaires Common Language Runtime (.resources) pouvant être incorporés dans un exécutable binaire runtime ou un assembly satellite. (Consultez [Création de fichiers de ressources](../resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe est un utilitaire de conversion des ressources à but général, qui effectue les tâches suivantes :  
  
- Il convertit les fichiers .txt ou .restext en fichiers .resources ou .resx. (Le format des fichiers .restext est identique à celui des fichiers .txt. Toutefois, l'extension .restext vous aide à identifier plus facilement les fichiers texte qui contiennent des définitions de ressource.)  
  
- Il convertit les fichiers .resources en fichiers .txt ou .resx ;  
  
- Il convertit les fichiers .resx en fichiers .txt ou .resources ;  
  
- Extrait les ressources de type chaîne d’un assembly dans un fichier. resw qui convient à une utilisation dans une application de Windows 8. x Store.  
  
- Il crée une classe fortement typée qui permet d'accéder aux ressources individuelles nommées et à l'instance <xref:System.Resources.ResourceManager>.  
  
 Si Resgen.exe échoue pour une raison quelconque, la valeur de retour sera -1.  
  
 Pour obtenir de l’aide sur Resgen. exe, vous pouvez utiliser la commande suivante, sans aucune option spécifiée, pour afficher la syntaxe de commande et les options de Resgen. exe :  
  
```console  
resgen  
```  
  
 Vous pouvez également utiliser l'option `/?` :  
  
```console  
resgen /?  
```  
  
 Si vous utilisez Resgen. exe pour générer des fichiers. resources binaires, vous pouvez utiliser un compilateur de langage pour incorporer les fichiers binaires dans des assemblys exécutables, ou vous pouvez utiliser [Assembly Linker (al. exe)](al-exe-assembly-linker.md) pour les compiler dans des assemblys satellites.  
  
 Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez :  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre ou option|Description|  
|-------------------------|-----------------|  
|`/define:` *symbol1*[, *symbol2*,...]|À compter de .NET Framework 4.5, prend en charge la compilation conditionnelle dans les fichiers de ressources au format texte (.txt ou .restext). Si *symbol* correspond à un symbole inclus dans le fichier texte d’entrée au sein d’une construction `#ifdef`, la ressource de chaîne associée est incluse dans le fichier .resources. Si le fichier texte d'entrée inclut une instruction `#if !` avec un symbole qui n'est pas défini par l'option, `/define`, la ressource de chaîne associée est incluse dans le fichier de ressources.<br /><br /> `/define` est ignorée si utilisée avec des fichiers au format autre que le format texte. Les symboles respectent la casse.<br /><br /> Pour plus d’informations sur cette option, consultez [Ressources de compilation conditionnelle](#Conditional) plus loin dans cette rubrique.|  
|`useSourcePath`|Précise que le répertoire actif du fichier d’entrée sera utilisé pour résoudre les chemins d’accès relatifs du fichier.|  
|`/compile`|Permet de spécifier plusieurs fichiers .resx ou texte à convertir en différents fichiers .resources en une seule opération globale. Si vous omettez cette option, vous ne pouvez spécifier qu’un seul argument de fichier d’entrée. Les fichiers de sortie sont nommés *nom_fichier*.resources.<br /><br /> Cette option ne peut pas être utilisée avec l'option `/str:`.<br /><br /> Pour plus d’informations sur cette option, consultez [Compilation ou conversion de plusieurs fichiers](#Multiple) plus loin dans cette rubrique.|  
|`/r:` `assembly`|Référence les métadonnées à partir de l'assembly spécifié. Cette option est utilisée lors de la conversion de fichiers .resx et permet à Resgen.exe de sérialiser ou de désérialiser des ressources d'objet. Elle est semblable à `/reference:` ou aux options `/r:` des compilateurs C# et Visual Basic.|  
|`filename.extension`|Spécifie le nom du fichier d'entrée à convertir. Si vous utilisez la première syntaxe de ligne de commande, plus longue, présentée avant ce tableau, `extension` doit être l'une des opérations suivantes :<br /><br /> .txt ou .restext<br /> Un fichier texte à convertir en fichier .resources ou .resx. Les fichiers texte ne peuvent comporter que des ressources de chaîne. Pour plus d’informations sur le format de fichier, consultez la section « Ressources dans les fichiers texte » de [Création de fichiers de ressources](../resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Un fichier de ressource XML à convertir en fichier .resources ou en fichier texte (.txt ou .restext).<br /><br /> .resources<br /> Un fichier de ressources binaire à convertir en fichier .resx ou en fichier texte (.txt ou .restext).<br /><br /> Si vous utilisez la deuxième syntaxe de ligne de commande, plus courte, présentée avant ce tableau, `extension` doit être la suivante :<br /><br /> .exe ou .dll<br /> Un .NET Framework assembly (exécutable ou bibliothèque) dont les ressources de chaîne doivent être extraites dans un fichier. resw pour une utilisation dans le développement d’applications du Windows 8. x Store.|  
|`outputFilename.extension`|Spécifie le nom et le type du fichier de ressources à créer.<br /><br /> Cet argument est facultatif lors de la conversion d'un fichier .txt, .restext ou .resx en un fichier .resources. Si vous ne spécifiez pas de valeur pour `outputFilename`, Resgen.exe ajoute une extension .resources à l'entrée `filename` et écrit le fichier dans le répertoire qui contient `filename,extension`.<br /><br /> L'argument `outputFilename.extension` est obligatoire lors d'une conversion à partir d'un fichier .resources. Spécifiez un nom de fichier avec l'extension .resx lors de la conversion d'un fichier .resources en fichier de ressources XML. Spécifiez un nom de fichier avec l'extension .txt ou .restext lors de la conversion d'un fichier .resources en fichier texte. Vous devez uniquement convertir un fichier .resources en fichier .txt lorsque le fichier .resources ne comporte que des valeurs de chaînes.|  
|`outputDirectory`|Pour les applications du Windows 8. x Store, spécifie le répertoire dans lequel un fichier. resw qui contient les ressources de chaîne dans `filename.extension` sera écrit. `outputDirectory` doit déjà exister.|  
|`/str:` `language[,namespace[,classname[,filename]]]`|Crée un fichier de la classe de ressource fortement typée dans le langage de programmation spécifié dans l'option `language`. `language` peut être un des littéraux suivants :<br /><br /> -   Pour C# : `c#`, `cs` ou `csharp`.<br />-   Pour Visual Basic : `vb` ou `visualbasic`.<br />-   Pour VBScript : `vbs` ou `vbscript`.<br />-   Pour C++ : `c++`, `mc` ou `cpp`.<br />-   Pour JavaScript : `js`, `jscript` ou `javascript`.<br /><br /> L'option `namespace` permet de spécifier l'espace de noms par défaut du projet, l'option `classname` permet de spécifier le nom de la classe générée et l'option `filename` permet de spécifier le nom du fichier de classe.<br /><br /> Un seul fichier d'entrée est autorisé lorsque l'option `/str:` est utilisée, afin qu'il ne puisse pas être utilisé avec l'option `/compile`.<br /><br /> Si `namespace` est spécifié, mais que `classname` ne l'est pas, le nom de la classe est dérivé du nom de fichier de sortie (par exemple, les traits de soulignement sont substitués pour les périodes). Les ressources fortement typées peuvent ne pas fonctionner correctement en conséquence. Pour éviter ce problème, spécifiez à la fois le nom de la classe et le nom du fichier de sortie.<br /><br /> Pour plus d’informations sur cette option, consultez [Génération d’une classe de ressource fortement typée](#Strong) plus loin dans cette rubrique.|  
|`/publicClass`|Crée une classe de ressource fortement typée en tant que classe publique. Par défaut, la classe de ressource en C# est `internal` et `Friend` en Visual Basic.<br /><br /> Cette option est ignorée si l'option `/str:` n'est pas utilisée.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Resgen.exe et les types de fichier de ressources  
 Pour que Resgen.exe convertisse correctement des ressources, les fichiers texte et .resx doivent respecter le bon format.  
  
### <a name="text-txt-and-restext-files"></a>Fichiers texte (.txt et .restext)  
 Les fichiers texte (.txt ou .restext) ne peuvent contenir que des ressources de chaîne. Les ressources de chaîne s'avèrent utiles lorsque vous écrivez une application dont les chaînes doivent être traduites dans plusieurs langues. Vous pouvez, par exemple, régionaliser les chaînes de menus à l'aide de la ressource de chaîne appropriée. Resgen.exe lit les fichiers texte comportant les paires nom/valeur, où le nom est une chaîne décrivant la ressource et la valeur est la chaîne de ressource elle-même.  
  
> [!NOTE]
> Pour plus d’informations sur les fichiers aux formats .txt et .restext, consultez la section « Ressources dans les fichiers texte » de [Création de fichiers de ressources](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Un fichier texte contenant des ressources doit être enregistré avec un encodage UTF-8 ou Unicode (UTF-16) à moins qu'il ne contienne uniquement des caractères de latin de base (U+007F). Resgen.exe supprime les caractères ANSI étendus lorsqu'il traite un fichier texte qui est enregistré avec l'encodage ANSI.  
  
 Resgen.exe recherche d'éventuels doublons de noms de ressources dans le fichier texte. Si le fichier texte contient des noms de ressources en double, Resgen.exe émettra un avertissement et ignorera la seconde valeur.  
  
### <a name="resx-files"></a>Fichiers .resx  
 Les fichiers de ressources au format .resx contiennent des entrées XML. Vous pouvez spécifier des ressources de chaîne dans ces entrées XML, comme dans les fichiers texte. Le principal avantage des fichiers .resx par rapport aux fichiers texte est que vous pouvez aussi spécifier ou incorporer des objets. Lorsque vous affichez un fichier .resx, il est possible de consulter la forme binaire d'un objet incorporé (une image, par exemple) si ces informations binaires sont intégrées au manifeste des ressources. Comme pour les fichiers texte, il est possible d'ouvrir un fichier .resx avec un éditeur de texte (tel que le Bloc-notes ou Microsoft Word) et écrire, analyser et manipuler son contenu. Notez que pour y parvenir, une bonne connaissance des étiquettes XML et de la structure des fichiers .resx s’avère nécessaire. Pour plus d’informations sur le format de fichier .resx, consultez la section « Ressources dans les fichiers .resx » de [Création de fichiers de ressources](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Pour créer un fichier .resources comportant des objets incorporés qui ne sont pas des chaînes, vous devez utiliser soit Resgen.exe pour convertir un fichier .resx contenant des objets ou ajouter les ressources de ces objet à votre fichier directement à partir du code, à l'aide des méthodes fournies par la classe <xref:System.Resources.ResourceWriter>.  
  
 Si votre fichier .resx ou .resources contient des objets et si vous utilisez Resgen.exe pour le convertir en fichier texte, toutes les ressources de chaîne seront converties correctement, mais les types de données des objets qui ne sont pas des chaînes seront également écrits dans le fichier sous forme de chaînes. Vous perdrez alors les objets incorporés au cours de la conversion et Resgen.exe signalera qu'une erreur s'est produite lors de la récupération des ressources.  
  
### <a name="converting-between-resources-file-types"></a>Conversion entre types de fichier de ressources  
 Lorsque vous effectuez une conversion entre différents types de fichier de ressources, il arrive que Resgen.exe ne puisse pas effectuer la conversion ou qu'il perde des informations sur des ressources spécifiques, selon les types de fichier source et cible. Le tableau suivant répertorie les types de conversions qui sont réussies lors de la conversion d'un type de fichier de ressources en un autre.  
  
|Convertir de|en fichier texte|en fichier .resx|en fichier .resw|en fichier .resources|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Fichier texte (.txt ou .restext)|--|Aucun problème|Non prise en charge|Aucun problème|  
|Fichier .resx|La conversion échoue si le fichier contient des ressources qui ne sont pas des chaînes (y compris les liens de fichier)|--|Non prise en charge|Aucun problème|  
|Fichier .resources|La conversion échoue si le fichier contient des ressources qui ne sont pas des chaînes (y compris les liens de fichier)|Aucun problème|Non prise en charge|--|  
|assembly .exe ou .dll|Non prise en charge|Non prise en charge|Seules les ressources de chaîne (y compris les noms de chemin d'accès) sont identifiées comme des ressources.|Non prise en charge|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Exécution de tâches spécifiques à Resgen.exe  
 Vous pouvez utiliser Resgen.exe de différentes façons : pour compiler un fichier de ressource texte ou XML dans un fichier binaire, pour effectuer des conversions entre plusieurs formats de fichier de ressources et pour générer une classe qui encapsule la fonctionnalité du <xref:System.Resources.ResourceManager> et fournit l'accès aux ressources. Cette section fournit des informations détaillées sur chaque tâche :  
  
- [Compilation de ressources dans un fichier binaire](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Conversion entre différents types de fichier de ressources](resgen-exe-resource-file-generator.md#Convert)  
  
- [Compilation ou conversion de plusieurs fichiers](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Exportation de ressources vers un fichier .resw](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Ressources de compilation conditionnelle](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Génération d’une classe de ressource fortement typée](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>
### <a name="compiling-resources-into-a-binary-file"></a>Compilation de ressources dans un fichier binaire  
 L'utilisation la plus courante de Resgen.exe consiste à compiler un fichier de ressources texte (un fichier .txt ou .restext) ou un fichier de ressources XML (fichier .resx) dans un fichier .resources binaire. Le fichier de sortie peut être alors incorporé dans un assembly principal par un compilateur de langage ou dans un assembly satellite par le biais d’[Assembly Linker (AL.exe)](al-exe-assembly-linker.md).  
  
 La syntaxe pour compiler un fichier de ressources est :  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 où les paramètres sont :  
  
 `inputFilename`  
 Le nom de fichier, y compris l’extension, du fichier de ressources à compiler. Resgen.exe compile uniquement des fichiers dont les extensions sont .txt, .restext, ou .resx.  
  
 `outputFilename`  
 Le nom du fichier de sortie. Si vous omettez `outputFilename`, Resgen.exe crée un fichier .resources avec le nom de fichier racine de `inputFilename` dans le même répertoire que `inputFilename`. Si `outputFilename` inclut un chemin d'accès, le répertoire doit exister.  
  
 Vous fournissez un espace de noms entièrement qualifié pour le fichier .resources en le spécifiant dans le nom du fichier et en le séparant du nom du fichier racine à l'aide d'un point. Par exemple, si `outputFilename` a la valeur `MyCompany.Libraries.Strings.resources`, l’espace de noms est MyCompany.Libraries.  
  
 La commande suivante lit les paires nom/valeur contenues dans Resources.txt et crée un fichier .ressources binaire nommé Resources.resources. Lorsque le nom du fichier de sortie n'est pas spécifié explicitement, il reçoit par défaut le même nom que le fichier d'entrée.  
  
```console  
resgen Resources.txt
```  
  
 La commande suivante lit les paires nom/valeur contenues dans Resources.restxt et crée un fichier de ressources binaire nommé StringResources.resources.  
  
```console  
resgen Resources.restext StringResources.resources  
```  
  
 La commande suivante lit un fichier d'entrée XML nommé Resources.resx et crée un fichier .resources binaire nommé Resources.resources.  
  
```console  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>
### <a name="converting-between-resource-file-types"></a>Conversion entre différents types de fichier de ressources  
 Outre le fait de compiler des fichiers ressources XML ou texte en fichiers .resources binaires, Resgen.exe peut convertir tout type de fichier compatible en tout autre type de fichier compatible. En d'autres termes, il peut exécuter les conversions suivantes :  
  
- fichiers .txt et .restext en fichiers .resx.  
  
- fichiers .resx en fichiers .txt et .restext.  
  
- fichiers .resources en fichiers .txt et .restext.  
  
- fichiers .resources en fichiers .resx.  
  
 La syntaxe est la même que celle représentée dans la section précédente.  
  
 En outre, vous pouvez utiliser Resgen. exe pour convertir des ressources incorporées dans un assembly de .NET Framework en un fichier. resw avec les applications du Windows 8. x Store.  
  
 La commande suivante lit un fichier de ressources binaire Resources.resources et crée un fichier de sortie XML nommé Resources.resx.  
  
```console  
resgen Resources.resources Resources.resx  
```  
  
 La commande suivante lit un fichier de ressources texte nommé StringResources.txt et crée un fichier de ressources XML nommé LibraryResources.resx. En plus de contenir des ressources de chaîne, le fichier .resx peut également être utilisé pour stocker des ressources autres que des chaînes.  
  
```console  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Les deux commandes suivantes lisent un fichier de ressources XML nommé Resources.resx et créent des fichiers texte nommés Resources.txt et Resources.restext. Notez que si le fichier .resx comporte des objets incorporés, ceux-ci ne seront pas correctement convertis en fichiers texte.  
  
```console  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>
### <a name="compiling-or-converting-multiple-files"></a>Compilation ou conversion de plusieurs fichiers  
 Vous pouvez utiliser l'option `/compile` pour convertir une liste de fichiers de ressources d'un format à un autre dans une opération unique. La syntaxe est :  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 La commande suivante compile trois fichiers, StringResources.txt, TableResources.resw, et ImageResources.resw, en des fichiers .resources séparés nommés StringResources.resources, TableResources.resources, et ImageResources.resources.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>
### <a name="exporting-resources-to-a-resw-file"></a>Exportation de ressources vers un fichier .resw  
 Si vous développez une application Windows 8. x Store, vous souhaiterez peut-être utiliser des ressources d’une application de bureau existante. Toutefois, les deux genres d'applications prennent en charge différents formats de fichier. Dans les applications de bureau, les ressources en texte (.txt ou .restext) ou les fichiers .resx sont compilés en fichiers binaires .resources. Dans les applications du Windows 8. x Store, les fichiers. resw sont compilés dans des fichiers d’index de ressources de package binaires (PRI). Vous pouvez utiliser Resgen. exe pour combler ce fossé en extrayant les ressources d’un fichier exécutable ou d’un assembly satellite et en les écrivant dans un ou plusieurs fichiers. resw qui peuvent être utilisés lors du développement d’une application Windows 8. x Store.  
  
> [!IMPORTANT]
> Visual Studio gère automatiquement toutes les conversions nécessaires pour incorporer les ressources d’une bibliothèque portable dans une application Windows 8. x Store. L’utilisation directe de Resgen. exe pour convertir les ressources d’un assembly au format de fichier. resw n’est intéressante que pour les développeurs qui souhaitent développer une application Windows 8. x Store en dehors de Visual Studio.  
  
 La syntaxe pour générer des fichiers .resw depuis un assembly est :  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 où les paramètres sont :  
  
 `filename.extension`  
 Le nom d'un assembly .NET Framework. (un fichier exécutable ou .dll). Si le fichier ne contient aucune ressource, Resgen.exe ne crée aucun fichier.  
  
 `outputDirectory`  
 Le répertoire existant dans lequel écrire les fichiers .resw. Si `outputDirectory` est omis, les fichiers .resw sont écrits dans le répertoire actif. Resgen.exe crée un fichier .resw pour chaque fichier .resources dans l'assembly. Le nom de fichier racine du fichier .resw est identique au nom racine du fichier .resources.  
  
 La commande suivante crée un fichier .resw dans le répertoire Win8Resources pour chaque fichier .resources incorporé dans MyApp.exe :  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>
### <a name="conditionally-compiling-resources"></a>Ressources de compilation conditionnelle  
 À compter de .NET Framework 4.5, Resgen.exe prend en charge la compilation conditionnelle des ressources de type chaîne dans des fichiers texte (.txt et .restext). Cela vous permet d'utiliser un fichier de ressources texte unique dans plusieurs configurations de build.  
  
 Dans un fichier .txt ou .restext, utilisez la construction `#ifdef`…`#endif` pour inclure une ressource dans le fichier .resources binaire si un symbole est défini, et utilisez la construction `#if !`... `#endif` pour inclure une ressource si aucun symbole n’est défini. Au moment de la compilation, vous définissez alors des symboles à l'aide de l'option `/define:` suivie d'une liste de symboles délimités par des virgules. La comparaison est sensible à la casse ; la casse des symboles définie par `/define` doit correspondre à la casse des symboles des fichiers texte à compiler.  
  
 Par exemple, le fichier suivant nommé UIResources.rext inclut une ressource de type chaîne de caractères nommée `AppTitle` qui peut prendre une valeurs sur trois, selon si les symboles nommés `PRODUCTION`, `CONSULT`, ou `RETAIL` sont définis.  
  
```text
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 Le fichier peut ensuite être compilé dans un fichier .resources binaire avec la commande suivante :  
  
```console  
resgen /define:CONSULT UIResources.restext  
```  
  
 Il en résulte un fichier .resources qui contient deux ressources de type chaîne de caractères. La valeur de la ressource `AppTitle` est "My Consulting Company Project Manager".  
  
<a name="Strong"></a>
### <a name="generating-a-strongly-typed-resource-class"></a>Génération d'une classe de ressource fortement typée  
 Resgen.exe prend en charge des ressources fortement typées, qui encapsulent l'accès aux ressources en créant des classes qui contiennent un jeu de propriétés statiques en lecture seule. Cela fournit une alternative à l'appel des méthodes de classe <xref:System.Resources.ResourceManager> directement pour récupérer des ressources. Il est possible d'activer la prise en charge des ressources fortement typées en utilisant l'option `/str` dans Resgen.exe, qui encapsule les fonctionnalités de la classe <xref:System.Resources.Tools.StronglyTypedResourceBuilder>. Lorsque vous spécifiez l'option `/str`, la sortie de Resgen.exe est une classe qui possède des propriétés fortement typées qui correspondent aux ressources qui sont référencées dans le paramètre d'entrée. Cette classe fournit un accès en lecture seule fortement typé aux ressources disponibles dans le fichier traité.  
  
 La syntaxe pour créer une ressource fortement typée est :  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Les paramètres et options sont :  
  
 `inputFilename`  
 Le nom de fichier, y compris l’extension, du fichier de ressources nécessitant de générer une classe de ressource fortement typée. Le fichier peut être un fichier texte, XML, ou .resources binaire pouvant avoir une extension .txt, .restext, .resw, ou .resources.  
  
 `outputFilename`  
 Le nom du fichier de sortie. Si `outputFilename` inclut un chemin d'accès, le répertoire doit exister. Si vous omettez `outputFilename`, Resgen.exe crée un fichier .resources avec le nom de fichier racine de `inputFilename` dans le même répertoire que `inputFilename`.  
  
 `outputFilename` peut être un fichier texte, XML ou un fichier .resources binaire. Si l'extension de fichier de `outputFilename` est différente de l'extension de fichier de `inputFilename`, Resgen.exe effectue une conversion de fichier.  
  
 Si `inputFilename` est un fichier .resources, Resgen.exe copie le fichier .resources si `outputFilename` est également un fichier .resources. Si `outputFilename` est omis, Resgen.exe remplace `inputFilename` par un fichier .resources identique.  
  
 *langue*  
 Langage dans lequel le code source doit être généré pour la classe de ressource fortement typée. Les valeurs possibles sont `cs`, `C#` et `csharp` pour le code C#, `vb` et `visualbasic` pour le code Visual Basic, `vbs` et `vbscript` pour le code VBScript, ainsi que `c++`, `mc` et `cpp` pour le code C++.  
  
 *namespace*  
 L'espace de noms qui contient la classe de ressource fortement typée. Le fichier .resources et la classe de ressource doivent avoir le même espace de noms. Pour plus d’informations sur la spécification de l’espace de noms dans `outputFilename`, consultez [Compilation de ressources dans un fichier binaire](resgen-exe-resource-file-generator.md#Compiling). Si *namespace* est omis, la classe de ressource n’est pas contenue dans un espace de noms.  
  
 *NomClasse*  
 Nom de la classe de ressource fortement typée. Cela doit correspondre au nom racine du fichier .resources. Par exemple, si Resgen.exe génère un fichier .resources nommé MyCompany.Libraries.Strings.resources, le nom de la classe de ressource fortement typée est Strings. Si *classname* est omis, la classe générée est dérivée du nom racine de `outputFilename`. Si `outputFilename` est omis, la classe générée est dérivée du nom racine de `inputFilename`.  
  
 *classname* ne peut pas contenir de caractères non valides, notamment des espaces incorporés. Si *classname* contient des espaces incorporés, ou si *classname* est généré par défaut à partir de *inputFilename* et que *inputFilename* contient des espaces incorporés, Resgen.exe remplace tous les caractères non valides par un trait de soulignement (\_).  
  
 *filename*  
 Nom du fichier de classe.  
  
 `/publicclass`  
 Rend public la classe de ressources fortement typée plutôt que `internal` (en C#) ou `Friend` (en Visual Basic). Cela permet d'accéder aux ressources depuis l'extérieur de l'assembly dans lequel elles sont incorporées.  
  
> [!IMPORTANT]
> Lorsque vous créez une classe de ressource fortement typé, le nom de votre fichier .resources doit correspondre à l'espace de noms et au nom de la classe du code généré. Toutefois, Resgen.exe vous permet de spécifier des options qui produisent un fichier .resources qui a un nom incompatible. Pour contourner ce comportement, renommez le fichier de sortie après qu'il ait été généré.  
  
 La classe de ressource fortement typée possède les entités suivantes :  
  
- Un constructeur sans paramètre, qui peut être utilisé pour instancier la classe de ressource fortement typée.  
  
- Une propriété `static` (C#) ou `Shared` (Visual Basic) et accessible en lecture seule du `ResourceManager`, qui retourne l'instance du <xref:System.Resources.ResourceManager>, qui gère la ressource fortement typée.  
  
- Une propriété `Culture` statique, qui vous permet de définir la culture utilisée pour la récupération de ressource. Par défaut, sa valeur est `null`, ce qui signifie que la culture d'interface utilisateur actuelle est utilisée.  
  
- Une propriété `static` (C#) ou `Shared` (Visual Basic) et en lecture seule pour chaque ressource du fichier .resources. La propriété porte le nom de la ressource. -  
  
 Par exemple, la commande suivante compile un fichier de ressources nommé StringResources.txt dans StringResources.resources et génère une classe nommée `StringResources` dans un fichier de code source Visual Basic nommé StringResources.vb qui peut être utilisé pour accéder au Gestionnaire des ressources.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a>Voir aussi

- [outils](index.md)
- [Ressources dans les applications de bureau](../resources/index.md)
- [Création de fichiers de ressources](../resources/creating-resource-files-for-desktop-apps.md)
- [Al. exe (Assembly Linker)](al-exe-assembly-linker.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
