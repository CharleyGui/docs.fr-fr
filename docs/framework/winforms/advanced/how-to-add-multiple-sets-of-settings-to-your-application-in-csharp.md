---
title: 'Comment : ajouter plusieurs jeux de paramètres à votre application en C#'
description: Découvrez comment ajouter plusieurs jeux de Windows Forms paramètres à votre application en C# à l’aide de Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173443"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="744be-103">Comment : ajouter plusieurs jeux de paramètres à votre application en C\#</span><span class="sxs-lookup"><span data-stu-id="744be-103">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="744be-104">Dans certains cas, vous souhaiterez peut-être avoir plusieurs jeux de paramètres dans une application.</span><span class="sxs-lookup"><span data-stu-id="744be-104">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="744be-105">Par exemple, si vous développez une application dans laquelle un groupe de paramètres particulier est censé changer fréquemment, il peut être judicieux de les séparer en un seul fichier afin que le fichier puisse être remplacé en gros, laissant les autres paramètres non affectés.</span><span class="sxs-lookup"><span data-stu-id="744be-105">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="744be-106">Visual Studio vous permet d’ajouter plusieurs jeux de paramètres à votre projet.</span><span class="sxs-lookup"><span data-stu-id="744be-106">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="744be-107">Des ensembles de paramètres supplémentaires sont accessibles via l' `Properties.Settings` objet.</span><span class="sxs-lookup"><span data-stu-id="744be-107">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="744be-108">Ajouter un ensemble supplémentaire de paramètres</span><span class="sxs-lookup"><span data-stu-id="744be-108">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="744be-109">Dans Visual Studio, dans le menu **projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="744be-109">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="744be-110">La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="744be-110">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="744be-111">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **fichier de paramètres**, entrez un nom pour le fichier, puis cliquez sur **Ajouter** pour ajouter un nouveau fichier de paramètres à votre solution.</span><span class="sxs-lookup"><span data-stu-id="744be-111">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="744be-112">Dans **Explorateur de solutions**, faites glisser le nouveau fichier de paramètres dans le dossier **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="744be-112">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="744be-113">Cela permet à vos nouveaux paramètres d’être disponibles dans le code.</span><span class="sxs-lookup"><span data-stu-id="744be-113">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="744be-114">Ajoutez et utilisez les paramètres de ce fichier comme vous le feriez pour tout autre fichier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="744be-114">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="744be-115">Vous pouvez accéder à ce groupe de paramètres via l' `Properties.Settings` objet.</span><span class="sxs-lookup"><span data-stu-id="744be-115">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="744be-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="744be-116">See also</span></span>

- [<span data-ttu-id="744be-117">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="744be-117">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="744be-118">Vue d’ensemble des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="744be-118">Application Settings Overview</span></span>](application-settings-overview.md)
