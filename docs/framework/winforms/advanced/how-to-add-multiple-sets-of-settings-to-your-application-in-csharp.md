---
title: 'Procédure : ajouter plusieurs jeux de paramètres à votre application en C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040127"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="a95e1-102">Procédure : Ajouter plusieurs jeux de paramètres à votre application en C\#</span><span class="sxs-lookup"><span data-stu-id="a95e1-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="a95e1-103">Dans certains cas, vous souhaiterez peut-être avoir plusieurs jeux de paramètres dans une application.</span><span class="sxs-lookup"><span data-stu-id="a95e1-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="a95e1-104">Par exemple, si vous développez une application dans laquelle un groupe de paramètres particulier est censé changer fréquemment, il peut être judicieux de les séparer en un seul fichier afin que le fichier puisse être remplacé en gros, laissant les autres paramètres non affectés.</span><span class="sxs-lookup"><span data-stu-id="a95e1-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="a95e1-105">Visual Studio vous permet d’ajouter plusieurs jeux de paramètres à votre projet.</span><span class="sxs-lookup"><span data-stu-id="a95e1-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="a95e1-106">Des ensembles de paramètres supplémentaires sont accessibles via l' `Properties.Settings` objet.</span><span class="sxs-lookup"><span data-stu-id="a95e1-106">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="a95e1-107">Ajouter un ensemble supplémentaire de paramètres</span><span class="sxs-lookup"><span data-stu-id="a95e1-107">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="a95e1-108">Dans Visual Studio, dans le menu **projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="a95e1-108">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="a95e1-109">La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="a95e1-109">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="a95e1-110">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **fichier de paramètres**, entrez un nom pour le fichier, puis cliquez sur **Ajouter** pour ajouter un nouveau fichier de paramètres à votre solution.</span><span class="sxs-lookup"><span data-stu-id="a95e1-110">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="a95e1-111">Dans **Explorateur de solutions**, faites glisser le nouveau fichier de paramètres dans le dossier **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="a95e1-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="a95e1-112">Cela permet à vos nouveaux paramètres d’être disponibles dans le code.</span><span class="sxs-lookup"><span data-stu-id="a95e1-112">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="a95e1-113">Ajoutez et utilisez les paramètres de ce fichier comme vous le feriez pour tout autre fichier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a95e1-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="a95e1-114">Vous pouvez accéder à ce groupe de paramètres via `Properties.Settings` l’objet.</span><span class="sxs-lookup"><span data-stu-id="a95e1-114">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="a95e1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a95e1-115">See also</span></span>

- [<span data-ttu-id="a95e1-116">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="a95e1-116">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="a95e1-117">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="a95e1-117">Application Settings Overview</span></span>](application-settings-overview.md)
