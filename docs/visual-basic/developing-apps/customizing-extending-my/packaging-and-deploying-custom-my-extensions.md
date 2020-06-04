---
title: Empaquetage et déploiement d’extensions My personnalisées
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 6d2cc2b01b04b30bd3b1a4371352ded20ea8664b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411751"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="86257-102">Empaqueter et déployer des extensions My personnalisées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86257-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="86257-103">Visual Basic offre un moyen simple de déployer vos `My` extensions d’espace de noms personnalisées à l’aide de modèles Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86257-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="86257-104">Si vous créez un modèle de projet pour lequel vos `My` Extensions font partie intégrante du nouveau type de projet, vous pouvez simplement inclure votre `My` code d’extension personnalisé avec le projet lorsque vous exportez le modèle.</span><span class="sxs-lookup"><span data-stu-id="86257-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="86257-105">Pour plus d’informations sur l’exportation de modèles de projet, consultez [Comment : créer des modèles de projet](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="86257-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="86257-106">Si votre `My` extension personnalisée se trouve dans un fichier de code unique, vous pouvez exporter le fichier en tant que modèle d’élément que les utilisateurs peuvent ajouter à n’importe quel type de Visual Basic projet.</span><span class="sxs-lookup"><span data-stu-id="86257-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="86257-107">Vous pouvez ensuite personnaliser le modèle d’élément pour activer des fonctionnalités et un comportement supplémentaires pour votre `My` extension personnalisée dans un projet de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86257-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="86257-108">Ces fonctionnalités sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="86257-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="86257-109">Autoriser les utilisateurs à gérer votre `My` extension personnalisée à partir de la page **Extensions My** du concepteur de projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86257-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="86257-110">Ajout automatique de votre `My` extension personnalisée lorsqu’une référence à un assembly spécifié est ajoutée à un projet.</span><span class="sxs-lookup"><span data-stu-id="86257-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="86257-111">Masquage du `My` modèle d’élément d’extension dans la boîte de dialogue **Ajouter un élément** afin qu’il ne soit pas inclus dans la liste d’éléments de projet.</span><span class="sxs-lookup"><span data-stu-id="86257-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="86257-112">Cette rubrique explique comment empaqueter une `My` extension personnalisée sous la forme d’un modèle d’élément masqué qui peut être géré à partir de la page **Extensions My** du concepteur de projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86257-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="86257-113">L' `My` extension personnalisée peut également être ajoutée automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet.</span><span class="sxs-lookup"><span data-stu-id="86257-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="86257-114">Créer une extension de l’espace de noms My</span><span class="sxs-lookup"><span data-stu-id="86257-114">Create a My namespace extension</span></span>

<span data-ttu-id="86257-115">La première étape de la création d’un package de déploiement pour une `My` extension personnalisée consiste à créer l’extension sous la forme d’un fichier de code unique.</span><span class="sxs-lookup"><span data-stu-id="86257-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="86257-116">Pour plus d’informations et pour obtenir des instructions sur la création d’une `My` extension personnalisée, consultez [extension de l’espace de noms My dans Visual Basic](extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="86257-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="86257-117">Exporter une extension de l’espace de noms My en tant que modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="86257-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="86257-118">Une fois que vous disposez d’un fichier de code qui comprend votre `My` extension d’espace de noms, vous pouvez exporter le fichier de code en tant que modèle d’élément Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86257-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="86257-119">Pour obtenir des instructions sur l’exportation d’un fichier en tant que modèle d’élément Visual Studio, consultez [Comment : créer des modèles d’élément](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="86257-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="86257-120">Si votre `My` extension d’espace de noms a une dépendance sur un assembly particulier, vous pouvez personnaliser votre modèle d’élément pour installer automatiquement votre `My` extension d’espace de noms lors de l’ajout d’une référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="86257-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="86257-121">Par conséquent, vous voudrez exclure cette référence d’assembly lorsque vous exportez le fichier de code en tant que modèle d’élément Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86257-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="86257-122">Personnaliser le modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="86257-122">Customize the item template</span></span>

<span data-ttu-id="86257-123">Vous pouvez activer votre modèle d’élément à gérer à partir de la page **Extensions My** du concepteur de projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86257-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="86257-124">Vous pouvez également activer le modèle d’élément à ajouter automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet.</span><span class="sxs-lookup"><span data-stu-id="86257-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="86257-125">Pour activer ces personnalisations, vous allez ajouter un nouveau fichier, appelé le fichier CustomData, à votre modèle, puis ajouter un nouvel élément au XML dans votre fichier. vstemplate.</span><span class="sxs-lookup"><span data-stu-id="86257-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="86257-126">Ajouter le fichier CustomData</span><span class="sxs-lookup"><span data-stu-id="86257-126">Add the CustomData file</span></span>

<span data-ttu-id="86257-127">Le fichier CustomData est un fichier texte dont l’extension de nom de fichier est. CustomData (le nom de fichier peut être défini sur n’importe quelle valeur significative pour votre modèle) et contient du code XML.</span><span class="sxs-lookup"><span data-stu-id="86257-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="86257-128">Le code XML du fichier CustomData indique à Visual Basic d’inclure votre `My` extension quand les utilisateurs utilisent la page **mes extensions** du concepteur de projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86257-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="86257-129">Vous pouvez éventuellement ajouter l’attribut <`AssemblyFullName>` à votre fichier XML CustomData.</span><span class="sxs-lookup"><span data-stu-id="86257-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="86257-130">Cela indique à Visual Basic d’installer automatiquement votre `My` extension personnalisée lorsqu’une référence à un assembly particulier est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="86257-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="86257-131">Vous pouvez utiliser n’importe quel éditeur de texte ou éditeur XML pour créer le fichier CustomData, puis l’ajouter au dossier compressé de votre modèle d’élément (fichier. zip).</span><span class="sxs-lookup"><span data-stu-id="86257-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="86257-132">Par exemple, le code XML suivant montre le contenu d’un fichier CustomData qui ajoute l’élément de modèle au dossier Mes extensions d’un projet Visual Basic lorsqu’une référence à l’assembly Microsoft. VisualBasic. PowerPacks. vs. dll est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="86257-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="86257-133">Le fichier CustomData contient un `VBMyExtensionTemplate>` élément <qui a des attributs comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="86257-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="86257-134">Attribut</span><span class="sxs-lookup"><span data-stu-id="86257-134">Attribute</span></span>|<span data-ttu-id="86257-135">Description</span><span class="sxs-lookup"><span data-stu-id="86257-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="86257-136">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="86257-136">Required.</span></span> <span data-ttu-id="86257-137">Identificateur unique de l’extension.</span><span class="sxs-lookup"><span data-stu-id="86257-137">A unique identifier for the extension.</span></span> <span data-ttu-id="86257-138">Si l’extension qui a cet ID a déjà été ajoutée au projet, l’utilisateur ne sera pas invité à l’ajouter à nouveau.</span><span class="sxs-lookup"><span data-stu-id="86257-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="86257-139">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="86257-139">Required.</span></span> <span data-ttu-id="86257-140">Numéro de version du modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="86257-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="86257-141">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="86257-141">Optional.</span></span> <span data-ttu-id="86257-142">Nom d'assembly</span><span class="sxs-lookup"><span data-stu-id="86257-142">An assembly name.</span></span> <span data-ttu-id="86257-143">Lorsqu’une référence à cet assembly est ajoutée au projet, l’utilisateur est invité à ajouter l' `My` extension à partir de ce modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="86257-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="86257-144">Ajouter l' \<CustomDataSignature> élément au fichier. vstemplate</span><span class="sxs-lookup"><span data-stu-id="86257-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="86257-145">Pour identifier votre modèle d’élément Visual Studio en tant qu' `My` extension d’espace de noms, vous devez également modifier le fichier. vstemplate pour votre modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="86257-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="86257-146">Vous devez ajouter un `<CustomDataSignature>` élément à l' `<TemplateData>` élément.</span><span class="sxs-lookup"><span data-stu-id="86257-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="86257-147">L' `<CustomDataSignature>` élément doit contenir le texte `Microsoft.VisualBasic.MyExtension` , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="86257-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="86257-148">Vous ne pouvez pas modifier directement des fichiers dans un dossier compressé (fichier. zip).</span><span class="sxs-lookup"><span data-stu-id="86257-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="86257-149">Vous devez copier le fichier. vstemplate à partir du dossier compressé, le modifier, puis remplacer le fichier. vstemplate dans le dossier compressé par votre copie mise à jour.</span><span class="sxs-lookup"><span data-stu-id="86257-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="86257-150">L’exemple suivant montre le contenu d’un fichier. vstemplate pour lequel l' `<CustomDataSignature>` élément a été ajouté.</span><span class="sxs-lookup"><span data-stu-id="86257-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="86257-151">Installer le modèle</span><span class="sxs-lookup"><span data-stu-id="86257-151">Install the template</span></span>

<span data-ttu-id="86257-152">Pour installer le modèle, vous pouvez copier le dossier compressé (fichier *. zip* ) dans le dossier modèles d’élément Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86257-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="86257-153">Par défaut, les modèles d’élément utilisateur se trouvent dans *%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="86257-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="86257-154">Vous pouvez également publier le modèle en tant que fichier Visual Studio Installer (*. vsi*).</span><span class="sxs-lookup"><span data-stu-id="86257-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="86257-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86257-155">See also</span></span>

- [<span data-ttu-id="86257-156">Extension de l’espace de noms My dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86257-156">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)
- [<span data-ttu-id="86257-157">Extension du modèle d'application Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86257-157">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="86257-158">Personnalisation de la disponibilité ou non des objets dans My</span><span class="sxs-lookup"><span data-stu-id="86257-158">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="86257-159">Page Mes extensions, Concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="86257-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
