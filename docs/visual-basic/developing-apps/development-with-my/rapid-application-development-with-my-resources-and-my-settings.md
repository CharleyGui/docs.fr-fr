---
title: Développement rapide d’application avec My.Resources et My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 6c53d11a3830a5a8a2cb898728bed8694a226686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411666"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="2fd29-102">Développement rapide d'application avec My.Resources et My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fd29-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="2fd29-103">L' `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de récupérer de manière dynamique des ressources pour votre application.</span><span class="sxs-lookup"><span data-stu-id="2fd29-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="2fd29-104">Récupération de ressources</span><span class="sxs-lookup"><span data-stu-id="2fd29-104">Retrieving Resources</span></span>  

 <span data-ttu-id="2fd29-105">Un certain nombre de ressources, telles que des fichiers audio, des icônes, des images et des chaînes, peuvent être récupérées par le biais de l' `My.Resources` objet.</span><span class="sxs-lookup"><span data-stu-id="2fd29-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="2fd29-106">Par exemple, vous pouvez accéder aux fichiers de ressources propres à la culture de l’application.</span><span class="sxs-lookup"><span data-stu-id="2fd29-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="2fd29-107">L’exemple suivant définit l’icône du formulaire sur l’icône nommée `Form1Icon` stockée dans le fichier de ressources de l’application.</span><span class="sxs-lookup"><span data-stu-id="2fd29-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="2fd29-108">L' `My.Resources` objet expose uniquement les ressources globales.</span><span class="sxs-lookup"><span data-stu-id="2fd29-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="2fd29-109">Il ne fournit pas d’accès aux fichiers de ressources associés aux formulaires.</span><span class="sxs-lookup"><span data-stu-id="2fd29-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="2fd29-110">Vous devez accéder aux ressources du formulaire à partir du formulaire.</span><span class="sxs-lookup"><span data-stu-id="2fd29-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="2fd29-111">De même, l' `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et de récupérer dynamiquement des paramètres de propriété et d’autres informations pour votre application.</span><span class="sxs-lookup"><span data-stu-id="2fd29-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="2fd29-112">Pour plus d’informations, consultez [My. Resources](../../language-reference/objects/my-resources-object.md) et [My. Settings (objet](../../language-reference/objects/my-settings-object.md)).</span><span class="sxs-lookup"><span data-stu-id="2fd29-112">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd29-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fd29-113">See also</span></span>

- [<span data-ttu-id="2fd29-114">My.Resources, objet</span><span class="sxs-lookup"><span data-stu-id="2fd29-114">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="2fd29-115">My.Settings, objet</span><span class="sxs-lookup"><span data-stu-id="2fd29-115">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="2fd29-116">Accessing Application Settings</span><span class="sxs-lookup"><span data-stu-id="2fd29-116">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
