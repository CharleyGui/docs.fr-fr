---
title: Empaquetage et déploiement d’extensions My personnalisées
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330258"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Empaqueter et déployer des extensions My personnalisées (Visual Basic)

Visual Basic offre un moyen simple de déployer vos extensions d’espace `My` de noms personnalisées à l’aide de modèles Visual Studio. Si vous créez un modèle de projet pour lequel vos `My` extensions font partie intégrante du nouveau type de projet, vous pouvez simplement inclure votre code `My` d’extension personnalisé avec le projet lorsque vous exportez le modèle. Pour plus d’informations sur l’exportation de modèles de projet, consultez [Comment : créer des modèles de projet](/visualstudio/ide/how-to-create-project-templates).

Si votre extension `My` personnalisée se trouve dans un fichier de code unique, vous pouvez exporter le fichier en tant que modèle d’élément que les utilisateurs peuvent ajouter à n’importe quel type de Visual Basic projet. Vous pouvez ensuite personnaliser le modèle d’élément pour activer des fonctionnalités et un comportement supplémentaires `My` pour votre extension personnalisée dans un projet de Visual Basic. Ces fonctionnalités sont les suivantes :

- Autoriser les utilisateurs à gérer votre `My` extension personnalisée à partir de la page **Extensions My** du concepteur de projet Visual Basic.

- Ajout automatique de votre `My` extension personnalisée lorsqu’une référence à un assembly spécifié est ajoutée à un projet.

- Masquage `My` du modèle d’élément d’extension dans la boîte de dialogue **Ajouter un élément** afin qu’il ne soit pas inclus dans la liste d’éléments de projet.

Cette rubrique explique comment empaqueter une extension `My` personnalisée sous la forme d’un modèle d’élément masqué qui peut être géré à partir de la page **Extensions My** du concepteur de projet Visual Basic. L’extension `My` personnalisée peut également être ajoutée automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet.

## <a name="create-a-my-namespace-extension"></a>Créer une extension de l’espace de noms My

La première étape de la création d’un package de déploiement `My` pour une extension personnalisée consiste à créer l’extension sous la forme d’un fichier de code unique. Pour plus d’informations et pour obtenir des instructions sur `My` la création d’une extension personnalisée, consultez [extension de l’espace de noms My dans Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exporter une extension de l’espace de noms My en tant que modèle d’élément

Une fois que vous disposez d’un fichier de `My` code qui comprend votre extension d’espace de noms, vous pouvez exporter le fichier de code en tant que modèle d’élément Visual Studio. Pour obtenir des instructions sur l’exportation d’un fichier en tant que modèle d’élément Visual Studio, consultez [Comment : créer des modèles d’élément](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Si votre `My` extension d’espace de noms a une dépendance sur un assembly particulier, vous pouvez personnaliser votre modèle d' `My` élément pour installer automatiquement votre extension d’espace de noms lors de l’ajout d’une référence à cet assembly. Par conséquent, vous voudrez exclure cette référence d’assembly lorsque vous exportez le fichier de code en tant que modèle d’élément Visual Studio.

## <a name="customize-the-item-template"></a>Personnaliser le modèle d’élément

Vous pouvez activer votre modèle d’élément à gérer à partir de la page **Extensions My** du concepteur de projet Visual Basic. Vous pouvez également activer le modèle d’élément à ajouter automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet. Pour activer ces personnalisations, vous allez ajouter un nouveau fichier, appelé le fichier CustomData, à votre modèle, puis ajouter un nouvel élément au XML dans votre fichier. vstemplate.

### <a name="add-the-customdata-file"></a>Ajouter le fichier CustomData

Le fichier CustomData est un fichier texte dont l’extension de nom de fichier est. CustomData (le nom de fichier peut être défini sur n’importe quelle valeur significative pour votre modèle) et contient du code XML. Le code XML du fichier CustomData indique à Visual Basic d’inclure votre `My` extension quand les utilisateurs utilisent la page **mes extensions** du concepteur de projets Visual Basic. Vous pouvez éventuellement ajouter l’attribut <`AssemblyFullName>` à votre fichier XML CustomData. Cela indique à Visual Basic d’installer automatiquement votre extension `My` personnalisée lorsqu’une référence à un assembly particulier est ajoutée au projet. Vous pouvez utiliser n’importe quel éditeur de texte ou éditeur XML pour créer le fichier CustomData, puis l’ajouter au dossier compressé de votre modèle d’élément (fichier. zip).

Par exemple, le code XML suivant montre le contenu d’un fichier CustomData qui ajoute l’élément de modèle au dossier Mes extensions d’un projet Visual Basic lorsqu’une référence à l’assembly Microsoft. VisualBasic. PowerPacks. vs. dll est ajoutée au projet.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

Le fichier CustomData contient un élément `VBMyExtensionTemplate>` <qui a des attributs comme indiqué dans le tableau suivant.

|Attribut|Description|
|---|---|
|`ID`|Obligatoire. Identificateur unique de l’extension. Si l’extension qui a cet ID a déjà été ajoutée au projet, l’utilisateur ne sera pas invité à l’ajouter à nouveau.|
|`Version`|Obligatoire. Numéro de version du modèle d’élément.|
|`AssemblyFullName`|Facultatif. Nom d'assembly Lorsqu’une référence à cet assembly est ajoutée au projet, l’utilisateur est invité à ajouter l' `My` extension à partir de ce modèle d’élément.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Ajouter l' \<élément CustomDataSignature> au fichier. vstemplate

Pour identifier votre modèle d’élément Visual Studio en `My` tant qu’extension d’espace de noms, vous devez également modifier le fichier. vstemplate pour votre modèle d’élément. Vous devez ajouter un `<CustomDataSignature>` élément à l' `<TemplateData>` élément. L' `<CustomDataSignature>` élément doit contenir le texte `Microsoft.VisualBasic.MyExtension`, comme indiqué dans l’exemple suivant.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Vous ne pouvez pas modifier directement des fichiers dans un dossier compressé (fichier. zip). Vous devez copier le fichier. vstemplate à partir du dossier compressé, le modifier, puis remplacer le fichier. vstemplate dans le dossier compressé par votre copie mise à jour.

L’exemple suivant montre le contenu d’un fichier. vstemplate pour lequel l' `<CustomDataSignature>` élément a été ajouté.

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a>Installer le modèle

Pour installer le modèle, vous pouvez copier le dossier compressé (fichier *. zip* ) dans le dossier modèles d’élément Visual Basic. Par défaut, les modèles d’élément utilisateur se trouvent dans *%USERPROFILE%\Documents\Visual\>Studio \<version \Templates\ItemTemplates\Visual Basic*. Vous pouvez également publier le modèle en tant que fichier Visual Studio Installer (*. vsi*).

## <a name="see-also"></a>Voir aussi

- [Extension de l’espace de noms My dans Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Extension du modèle d’application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Page Mes extensions, Concepteur de projets](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
