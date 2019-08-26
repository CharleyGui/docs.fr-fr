---
title: 'Procédure : rendre persistants les paramètres utilisateur en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 0683a5c359da1c4d082f7312c1ed8f43e1c151f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968380"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="d6c10-102">Procédure : rendre persistants les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6c10-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="d6c10-103">Vous pouvez utiliser la méthode `My.Settings.Save` pour rendre persistantes les modifications apportées aux paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d6c10-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="d6c10-104">En règle générale, les applications sont conçues pour rendre persistantes les modifications apportées aux paramètres utilisateur quand l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="d6c10-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="d6c10-105">Cela est dû au fait que l’enregistrement des paramètres peut prendre, en fonction de plusieurs facteurs, plusieurs secondes.</span><span class="sxs-lookup"><span data-stu-id="d6c10-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="d6c10-106">Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="d6c10-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6c10-107">Bien que vous puissiez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l’exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programmation.</span><span class="sxs-lookup"><span data-stu-id="d6c10-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="d6c10-108">Vous pouvez changer les paramètres de portée application lors de la création de l’application, par l’intermédiaire du **Concepteur de projet**, ou en modifiant le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="d6c10-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="d6c10-109">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d6c10-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6c10-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="d6c10-110">Example</span></span>  
 <span data-ttu-id="d6c10-111">Cet exemple change la valeur du paramètre utilisateur `LastChanged` et enregistre cette modification en appelant la méthode `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="d6c10-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="d6c10-112">Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `LastChanged`, de type `Date`.</span><span class="sxs-lookup"><span data-stu-id="d6c10-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="d6c10-113">Pour plus d'informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d6c10-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c10-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6c10-114">See also</span></span>

- [<span data-ttu-id="d6c10-115">My.Settings (objet)</span><span class="sxs-lookup"><span data-stu-id="d6c10-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="d6c10-116">Guide pratique pour lire des paramètres d’application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6c10-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="d6c10-117">Guide pratique pour modifier les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6c10-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="d6c10-118">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6c10-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="d6c10-119">Gestion des paramètres d’une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="d6c10-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
