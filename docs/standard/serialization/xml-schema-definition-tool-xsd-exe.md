---
title: Outil XML Schema Definition (Xsd.exe)
description: Le générateur de sérialiseur XML crée un assembly de sérialisation XML pour les types dans un assembly spécifié, ce qui améliore les performances de démarrage de XmlSerializer.
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 0275ecfebd427feb104013024654d4a0bc98748a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288977"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>Outil XML Schema Definition (Xsd.exe)

L'outil XML Schema Definition Tool (Xsd.exe) génère des classes du Common Language Runtime et du schéma XML à partir de fichiers XDR, XML et XSD ou de classes figurant dans un assembly de runtime.

L’outil XML Schema Definition (XSD. exe) se trouve généralement à l’emplacement suivant : \
_C : \\ Program Files (x86) \\ Microsoft SDK \\ Windows \\ {version} \\ bin \\ netfx {version} Tools\\_

## <a name="syntax"></a>Syntaxe

Exécutez l’outil à partir de la ligne de commande.

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> Pour que .NET Framework outils fonctionnent correctement, vous devez définir `Path` correctement les `Include` variables d' `Lib` environnement, et. Définissez ces variables d’environnement en exécutant SDKVars. bat, qui se trouve dans le \<SDK> répertoire \v2.0\Bin. SDKVars.bat doit être exécuté dans chaque interpréteur de commandes.

## <a name="argument"></a>Argument

|Argument|Description|
|--------------|-----------------|
|*fichier. extension*|Spécifie le fichier d'entrée à convertir. Vous devez spécifier l’extension de l’une des manières suivantes :. XDR,. xml,. xsd,. dll ou. exe.<br /><br /> Si vous spécifiez un fichier de schéma XDR (extension .xdr), Xsd.exe convertit alors le schéma XDR en schéma XSD. Le fichier de sortie porte le même nom que celui du schéma XDR, mais son extension est .xsd.<br /><br /> Si vous spécifiez un fichier XML (extension .xml), Xsd.exe déduit alors un schéma à partir des données d'un fichier et génère un schéma XSD. Le fichier de sortie porte le même nom que celui du fichier XML, mais son extension est .xsd.<br /><br /> Si vous spécifiez un fichier de schéma XML (extension .xsd), Xsd.exe génère alors du code source pour les objets de runtime correspondant au schéma XML.<br /><br /> Si vous spécifiez un fichier d'assembly de runtime (extension .exe ou .dll), Xsd.exe génère alors des schémas pour un ou plusieurs types de cet assembly. Vous pouvez utiliser l'option `/type` pour spécifier les types pour lesquels générer des schémas. Les schémas de sortie sont nommés schema0.xsd, schema1.xsd, et ainsi de suite. Xsd.exe génère plusieurs schémas uniquement dans le cas où les types indiqués spécifieraient un espace de noms à l'aide de l'attribut personnalisé `XMLRoot`.|

## <a name="general-options"></a>Options générales

|Option|Description|
|------------|-----------------|
|**/h \[\]**|Affiche la syntaxe et les options de commande de l'outil.|
|**/o \[ utputdir \] :**_répertoire_|Spécifie le répertoire des fichiers de sortie. Cet argument ne peut être spécifié qu'à une seule reprise. L'emplacement par défaut est le répertoire actif.|
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|
|**/p \[ arameters \] :**_file. xml_|Options de lecture pour différents modes d'opération à partir du fichier .xml spécifié. La forme abrégée est `/p:`. Pour plus d’informations, consultez la section [Notes](#remarks) .|

## <a name="xsd-file-options"></a>Options de fichier XSD
 Vous ne devez spécifier qu'une seule des options suivantes pour les fichiers .xsd.

|Option|Description|
|------------|-----------------|
|**/c \[ lasses\]**|Génère des classes correspondant au schéma spécifié. Pour lire les données XML dans l’objet, utilisez la méthode <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType>.|
|**/d \[ ataset\]**|Génère une classe dérivée de <xref:System.Data.DataSet> qui correspond au schéma spécifié. Pour lire les données XML dans la classe dérivée, utilisez la méthode <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType>.|

 Vous pouvez également spécifier les options suivantes pour les fichiers .xsd.

|Option|Description|
|------------|-----------------|
|**/e \[ face \] :**_élément_|Spécifie l'élément figurant dans le schéma pour lequel générer du code. Tous les éléments sont par défaut tapés. Vous pouvez spécifier cet argument à plusieurs reprises.|
|**/enableDataBinding**|Implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> sur tous les types générés pour activer la liaison de données. La forme abrégée est `/edb`.|
|**/enableLinqDataSet**|(Forme abrégée : `/eld` .) Spécifie que le DataSet généré peut être interrogé sur l’utilisation de LINQ to DataSet. Cette option est utilisée lorsque l'option  /dataset est également spécifiée. Pour plus d’informations, consultez [Présentation de LINQ to DataSet](../../framework/data/adonet/linq-to-dataset-overview.md) et [Interrogation de datasets typés](../../framework/data/adonet/querying-typed-datasets.md). Pour obtenir des informations générales sur l’utilisation de LINQ, consultez [Language-Integrated Query (LINQ)-C#](../../csharp/programming-guide/concepts/linq/index.md) ou [Language-Integrated Query (linq)-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).|
|**/f \[ ields\]**|Génère des champs plutôt que des propriétés. Par défaut, des propriétés sont générées.|
|**/l \[ anguage \] :**_langage_|Spécifie le langage de programmation à utiliser. Vous avez le choix entre `CS` (C#, qui est la valeur par défaut), `VB` (Visual Basic), `JS` (JScript) ou `VJS` (Visual J#). Vous pouvez également spécifier un nom qualifié complet pour une classe implémentant <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.|
|**/n \[ amespace \] :**_espace de noms_|Spécifie l'espace de noms du runtime pour les types générés. L'espace de noms par défaut est `Schemas`.|
|**/nologo**|Supprime la bannière.|
|**/Order**|Génère des identificateurs d'ordre explicites sur les membres de particule.|
|**/o \[ ut \] :**_DirectoryName_|Spécifie le répertoire de sortie dans lequel placer les fichiers. L'emplacement par défaut est le répertoire actif.|
|**/u \[ RI \] :**_URI_|Spécifie l'URI des éléments figurant dans le schéma pour lequel générer du code. S'il existe, cet URI s'applique à tous les éléments spécifiés avec l'option `/element`.|

## <a name="dll-and-exe-file-options"></a>Options de fichier DLL et EXE

|Option|Description|
|------------|-----------------|
|**/t \[ ype \] :**_TypeName_|Spécifie le nom du type pour lequel créer un schéma. Vous pouvez spécifier plusieurs arguments pour le type. Si *nom_type* ne spécifie pas d’espace de noms, Xsd.exe établit une correspondance entre tous les types de l’assembly et le type spécifié. Si *nom_type* spécifie un espace de noms, une correspondance est établie uniquement avec ce type. Si *nom_type* se termine par un astérisque (\*), l’outil établit une correspondance avec tous les types commençant par la chaîne qui précède \*. Si vous omettez l'option `/type`, Xsd.exe génère alors des schémas pour tous les types de l'assembly.|

## <a name="remarks"></a>Remarques

Le tableau suivant affiche les opérations que Xsd.exe exécute.

| | |
|------------|-----------------|
|De XDR en XSD|Génère un schéma XML à partir d'un fichier de schéma XDR (XML-Data-Reduced). XDR est l'un des premiers formats de schéma XML.|
|De XML en XSD|Génère un schéma XML à partir d'un fichier XML.|
|De XSD en DataSet|Génère des classes <xref:System.Data.DataSet> de Common Language Runtime à partir d'un fichier de schéma XSD. Les classes générées proposent un modèle objet riche aux données XML régulières.|
|De XSD en classes|Génère des classes de runtime à partir d'un fichier de schéma XSD. Les classes générées peuvent être associées à <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> pour lire et écrire du code XML conforme au schéma.|
|De classes en XSD| Génère un schéma XML à partir d'un ou de plusieurs types dans un fichier d'assembly de runtime. Le schéma généré définit le format XML utilisé par le <xref:System.Xml.Serialization.XmlSerializer> .|

 Xsd.exe vous permet uniquement de manipuler les schémas XML conformes au langage XSD (XML Schema Definition) proposé par W3C (World Wide Web Consortium). Pour plus d’informations sur la proposition de définition de schéma XML ou la norme XML, consultez <https://w3.org> .

## <a name="setting-options-with-an-xml-file"></a>Définition d'options avec un fichier XML

À l’aide du commutateur `/parameters`, vous pouvez spécifier un fichier XML qui définit plusieurs options. Les options que vous pouvez définir dépendent de votre utilisation de l'outil XSD.exe. Les choix incluent la génération de schémas, la génération de fichiers de code ou la génération de fichiers de code qui incluent des fonctionnalités `DataSet`. Par exemple, vous pouvez définir l'élément `<assembly>` sur le nom d'un fichier exécutable (.exe) ou d'un fichier bibliothèque de types (.dll) lors de la génération d'un schéma, mais pas lors de la génération d'un fichier de code. Le code XML suivant indique comment utiliser l'élément `<generateSchemas>` avec un fichier exécutable spécifié :

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

Si le code XML précédent est contenu dans un fichier nommé GenerateSchemas. xml, utilisez le `/parameters` commutateur en tapant ce qui suit à l’invite de commandes et en appuyant sur **entrée**:

```console
 xsd /p:GenerateSchemas.xml
```

En revanche, si vous générez un schéma pour un seul type trouvé dans l'assembly, vous pouvez utiliser le code XML suivant :

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

Mais pour utiliser le code précédent, vous devez également fournir le nom de l'assembly à l'invite de commandes. Entrez ce qui suit à l’invite de commandes (en supposant que le fichier XML se nomme GenerateSchemaFromType. Xml) :

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

Vous ne devez spécifier qu'une seule des options suivantes pour l'élément `<generateSchemas>`.

|Élément|Description|
|-------------|-----------------|
|\<assembly>|Spécifie un assembly à partir duquel générer le schéma.|
|\<type>|Spécifie un type trouvé dans un assembly pour lequel générer un schéma.|
|\<xml>|Spécifie un fichier XML pour lequel générer un schéma.|
|\<xdr>|Spécifie un fichier XDR pour lequel générer un schéma.|

Pour générer un fichier de code, utilisez l'élément `<generateClasses>`. L'exemple suivant génère un fichier de code. Notez que deux attributs sont également indiqués, ils vous permettent de définir le langage de programmation et l'espace de noms du fichier généré.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 Les options que vous pouvez définir pour l'élément `<generateClasses>` incluent les éléments suivants.

|Élément|Description|
|-------------|-----------------|
|\<element>|Spécifie un élément dans le fichier .xsd pour lequel générer du code.|
|\<schemaImporterExtensions>|Spécifie un type dérivé de la classe <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>.|
|\<schema>|Spécifie un fichier de schéma XML pour lequel générer du code. Plusieurs fichiers de schéma XML peuvent être spécifiés à l’aide de plusieurs \<schema> éléments.|

Le tableau suivant affiche les attributs qui peuvent également être utilisés avec l'élément `<generateClasses>`.

|Attribut|Description|
|---------------|-----------------|
|langage|Spécifie le langage de programmation à utiliser. Vous avez le choix entre `CS` (C#, la valeur par défaut), `VB` (Visual Basic), `JS` (JScript) ou `VJS` (Visual J#). Vous pouvez également spécifier un nom qualifié complet pour une classe qui implémente <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|espace de noms|Spécifie l'espace de noms pour le code généré. L'espace de noms doit se conformer aux normes CLR (par exemple, aucun espace ou barre oblique inverse).|
|options|L’une des valeurs suivantes : `none`, `properties` (génère des propriétés au lieu de champs publics), `order` ou `enableDataBinding` (consultez les commutateurs `/order` et `/enableDataBinding` dans la section Options de fichier XSD précédente).|

 Vous pouvez également contrôler comment le code `DataSet` est généré à l'aide de l'élément `<generateDataSet>`. Le code XML suivant spécifie que le code généré utilise `DataSet` des structures (telles que la <xref:System.Data.DataTable> classe) pour créer Visual Basic code pour un élément spécifié. Les structures DataSet générées prendront en charge les requêtes LINQ.

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

Les options que vous pouvez définir pour l'élément `<generateDataSet>` incluent les éléments suivants.

|Élément|Description|
|-------------|-----------------|
|\<schema>|Spécifie un fichier de schéma XML pour lequel générer du code. Plusieurs fichiers de schéma XML peuvent être spécifiés à l’aide de plusieurs \<schema> éléments.|

 Le tableau suivant affiche les attributs qui peuvent être utilisés avec l'élément `<generateDataSet>`.

|Attribut|Description|
|---------------|-----------------|
|enableLinqDataSet|Spécifie que le DataSet généré peut être interrogé par rapport à l'utilisation de LINQ to DataSet. La valeur par défaut est false.|
|langage|Spécifie le langage de programmation à utiliser. Vous avez le choix entre `CS` (C#, la valeur par défaut), `VB` (Visual Basic), `JS` (JScript) ou `VJS` (Visual J#). Vous pouvez également spécifier un nom qualifié complet pour une classe qui implémente <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|espace de noms|Spécifie l'espace de noms pour le code généré. L'espace de noms doit se conformer aux normes CLR (par exemple, aucun espace ou barre oblique inverse).|

 Vous pouvez définir certains attributs sur l'élément `<xsd>` de niveau supérieur. Ces options peuvent être utilisées avec n'importe lequel des éléments enfants (`<generateSchemas>`, `<generateClasses>` ou `<generateDataSet>`). Le code XML suivant génère le code pour un élément nommé "IDItems" dans le répertoire de sortie nommé "MyOutputDirectory".

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

Le tableau suivant affiche les attributs qui peuvent également être utilisés avec l'élément `<xsd>`.

|Attribut|Description|
|---------------|-----------------|
|sortie|Le nom d'un répertoire dans lequel le schéma généré ou le fichier de code sera placé.|
|nologo|Supprime la bannière. A la valeur `true` ou `false`.|
|help|Affiche la syntaxe et les options de commande de l'outil. A la valeur `true` ou `false`.|

## <a name="examples"></a>Exemples
 La commande suivante génère un schéma XML à partir de `myFile.xdr` et l'enregistre dans le répertoire actif.

```console
xsd myFile.xdr
```

La commande suivante génère un schéma XML à partir de `myFile.xml` et l'enregistre dans le répertoire spécifié.

```console
xsd myFile.xml /outputdir:myOutputDir
```

La commande suivante génère un groupe de données qui correspond au schéma spécifié dans le langage C# et le sauvegarde comme `XSDSchemaFile.cs` dans le répertoire actif.

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

La commande suivante génère des schémas XML pour tous les types de l'assembly `myAssembly.dll` et les enregistre sous `schema0.xsd` dans le répertoire actif.

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [outils](../../framework/tools/index.md)
- [Invites de commandes](../../framework/tools/developer-command-prompt-for-vs.md)
- [Vue d'ensemble de LINQ to DataSet](../../framework/data/adonet/linq-to-dataset-overview.md)
- [Interrogation de DataSets typés](../../framework/data/adonet/querying-typed-datasets.md)
- [LINQ (Language-Integrated Query) (C#)](../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/index.md)
