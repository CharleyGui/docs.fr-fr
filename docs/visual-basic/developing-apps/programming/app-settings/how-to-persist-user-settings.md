---
title: 'Procédure : rendre persistants les paramètres utilisateur'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 817111060259bdfbbb26d9f8eafeae439e1f651f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410151"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="09597-102">Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09597-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="09597-103">Vous pouvez utiliser la méthode `My.Settings.Save` pour rendre persistantes les modifications apportées aux paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="09597-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="09597-104">En règle générale, les applications sont conçues pour rendre persistantes les modifications apportées aux paramètres utilisateur quand l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="09597-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="09597-105">Cela est dû au fait que l’enregistrement des paramètres peut prendre, en fonction de plusieurs facteurs, plusieurs secondes.</span><span class="sxs-lookup"><span data-stu-id="09597-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="09597-106">Pour plus d’informations, consultez [My.Settings, objet](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="09597-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09597-107">Bien que vous puissiez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l’exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programmation.</span><span class="sxs-lookup"><span data-stu-id="09597-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="09597-108">Vous pouvez changer les paramètres de portée application lors de la création de l’application, par l’intermédiaire du **Concepteur de projet**, ou en modifiant le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="09597-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="09597-109">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="09597-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09597-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="09597-110">Example</span></span>  

 <span data-ttu-id="09597-111">Cet exemple change la valeur du paramètre utilisateur `LastChanged` et enregistre cette modification en appelant la méthode `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="09597-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="09597-112">Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `LastChanged`, de type `Date`.</span><span class="sxs-lookup"><span data-stu-id="09597-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="09597-113">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="09597-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09597-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09597-114">See also</span></span>

- [<span data-ttu-id="09597-115">My.Settings, objet</span><span class="sxs-lookup"><span data-stu-id="09597-115">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="09597-116">Guide pratique pour lire des paramètres d’application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09597-116">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="09597-117">Guide pratique pour modifier les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09597-117">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="09597-118">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09597-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="09597-119">Gestion des paramètres d'une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="09597-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
