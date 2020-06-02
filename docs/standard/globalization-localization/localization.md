---
title: Localisation
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 68e877088c5c3d17b368561b563b4cb17d004e75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278023"
---
# <a name="localization"></a><span data-ttu-id="84bd5-102">Localisation</span><span class="sxs-lookup"><span data-stu-id="84bd5-102">Localization</span></span>

<span data-ttu-id="84bd5-103">La localisation correspond au processus de traduction des ressources d’une application dans des versions localisées pour chaque culture prise en charge par l’application.</span><span class="sxs-lookup"><span data-stu-id="84bd5-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="84bd5-104">Vous devez passer à l’étape de localisation uniquement après avoir effectué l’étape [Révision de l’adaptabilité](localizability-review.md) pour vérifier que l’application globalisée est prête pour la localisation.</span><span class="sxs-lookup"><span data-stu-id="84bd5-104">You should proceed to the localization step only after completing the [Localizability Review](localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="84bd5-105">Une application prête pour la localisation est divisée en deux blocs conceptuels, un bloc qui contient tous les éléments d’interface utilisateur et un bloc qui contient le code exécutable.</span><span class="sxs-lookup"><span data-stu-id="84bd5-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="84bd5-106">Le bloc d’interface utilisateur contient uniquement les éléments d’interface utilisateur localisables, comme les chaînes, les messages d’erreur, les boîtes de dialogue, les menus, les ressources d’objet incorporées, etc. relatifs à la culture neutre.</span><span class="sxs-lookup"><span data-stu-id="84bd5-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="84bd5-107">Le bloc de code contient uniquement le code d’application à utiliser par toutes les cultures prises en charge.</span><span class="sxs-lookup"><span data-stu-id="84bd5-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="84bd5-108">Le CLR prend en charge un modèle de ressource d’assembly satellite qui sépare le code exécutable d’une application de ses ressources.</span><span class="sxs-lookup"><span data-stu-id="84bd5-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="84bd5-109">Pour plus d’informations sur l’implémentation de ce modèle, consultez [Ressources dans .NET](../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="84bd5-109">For more information about implementing this model, see [Resources in .NET](../../framework/resources/index.md).</span></span>

<span data-ttu-id="84bd5-110">Pour chaque version localisée de votre application, ajoutez un nouvel assembly satellite contenant le bloc d’interface utilisateur localisée traduit dans la langue appropriée pour la culture cible.</span><span class="sxs-lookup"><span data-stu-id="84bd5-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="84bd5-111">Le bloc de code pour toutes les cultures doit rester le même.</span><span class="sxs-lookup"><span data-stu-id="84bd5-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="84bd5-112">La combinaison d’une version localisée du bloc d’interface utilisateur et du bloc de code produit une version localisée de votre application.</span><span class="sxs-lookup"><span data-stu-id="84bd5-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="84bd5-113">Le SDK Windows fournit le Windows Forms Resource Editor (Winres.exe), qui vous permet de localiser rapidement des Windows Forms pour les cultures cibles.</span><span class="sxs-lookup"><span data-stu-id="84bd5-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="84bd5-114">Pour plus d’informations sur l’utilisation de cet outil, consultez [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="84bd5-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84bd5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84bd5-115">See also</span></span>

- [<span data-ttu-id="84bd5-116">Globalisation et localisation</span><span class="sxs-lookup"><span data-stu-id="84bd5-116">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="84bd5-117">Revue de l’adaptabilité</span><span class="sxs-lookup"><span data-stu-id="84bd5-117">Localizability Review</span></span>](localizability-review.md)
- [<span data-ttu-id="84bd5-118">Globalisation</span><span class="sxs-lookup"><span data-stu-id="84bd5-118">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="84bd5-119">Ressources dans les applications de bureau</span><span class="sxs-lookup"><span data-stu-id="84bd5-119">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
