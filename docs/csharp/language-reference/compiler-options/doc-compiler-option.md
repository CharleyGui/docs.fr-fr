---
description: -doc (Options du compilateur C#)
title: -doc (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: e55b86e5b028fb871f309d80217477cfd164c106
ms.sourcegitcommit: f0eb7eeedf3ceec726499fa678786d03083214ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98629252"
---
# <a name="-doc-c-compiler-options"></a>-doc (Options du compilateur C#)

L’option **-doc** vous permet de placer des commentaires de documentation dans un fichier XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  

 `file`  
 Fichier de sortie XML, qui est rempli avec les commentaires des fichiers de code source de la compilation.  
  
## <a name="remarks"></a>Notes  

 Dans les fichiers de code source, les commentaires de documentation qui précèdent les éléments suivants peuvent être traités et ajoutés au fichier XML :  
  
- Types définis par l’utilisateur, tels qu’une [classe](../keywords/class.md), un [délégué](../builtin-types/reference-types.md#the-delegate-type) ou une [interface](../keywords/interface.md)  
  
- Membres tels qu’un champ, un [événement](../keywords/event.md), une [propriété](../../programming-guide/classes-and-structs/using-properties.md) ou une méthode  
  
 Le fichier de code source qui contient Main est sorti en premier dans le document XML.  
  
 Pour utiliser le fichier .xml généré avec la fonctionnalité [IntelliSense](/visualstudio/ide/using-intellisense), faites en sorte que le nom du fichier .xml soit identique à l’assembly que vous souhaitez prendre en charge, puis vérifiez que le fichier .xml est dans le même répertoire que l’assembly. Ainsi, quand l’assembly est référencé dans le projet Visual Studio, le fichier .xml est également trouvé. Pour plus d’informations, consultez [Insertion de commentaires dans le code XML](/visualstudio/ide/reference/generate-xml-documentation-comments).  
  
 Sauf si vous compilez avec [-target : module](./target-module-compiler-option.md), `file` contient des \<assembly> \</assembly> balises qui spécifient le nom du fichier contenant le manifeste d’assembly pour le fichier de sortie de la compilation.  
  
> [!NOTE]
> L’option -doc s’applique à tous les fichiers d’entrée ou, si elle est définie dans les paramètres de projet, à tous les fichiers du projet. Pour désactiver les avertissements relatifs aux commentaires de documentation pour un fichier ou une section de code spécifique, utilisez [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Pour découvrir comment générer de la documentation à partir de commentaires dans votre code, consultez [Balises recommandées pour les commentaires de documentation](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-2019-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio 2019  

1. Ouvrez la page **Propriétés** du projet.  
2. Cliquez sur l’onglet **Générer**.
3. Modifiez la propriété **Fichier de documentation XML**.
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-for-mac-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio pour Mac  
  
1. Ouvrez la page d' **options** du projet.
2. Sélectionnez l’onglet **compilateur** .
3. Sélectionnez **générer la documentation XML** et entrez le nom du fichier dans la zone de texte.

Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
