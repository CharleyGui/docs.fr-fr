---
title: 'Guide pratique : modifier les paramètres utilisateur'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329627"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="5b1a9-102">Guide pratique pour modifier les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b1a9-102">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="5b1a9-103">Vous pouvez modifier un paramètre utilisateur en assignant une nouvelle valeur à la propriété du paramètre de l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="5b1a9-104">L’objet `My.Settings` expose chaque paramètre en tant que propriété.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5b1a9-105">Le nom de la propriété est le même que le nom du paramètre, et le type de la propriété est le même que le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5b1a9-106">La **portée** du paramètre détermine si la propriété est lue uniquement : La propriété **d’un**paramètre d’application-portée est lue uniquement, tandis que la propriété d’un paramètre **d’utilisation utilisateur-scope**est lue.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="5b1a9-107">Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5b1a9-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b1a9-108">Bien que vous puissiez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l’exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programmation.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="5b1a9-109">Vous pouvez changer les paramètres de portée application lors de la création de l’application, à l’aide du **Concepteur de projet**, ou en modifiant le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="5b1a9-110">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5b1a9-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b1a9-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5b1a9-111">Example</span></span>  

 <span data-ttu-id="5b1a9-112">Dans cet exemple, la valeur du paramètre utilisateur `Nickname` est modifiée.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="5b1a9-113">Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `Nickname`, de type `String`.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="5b1a9-114">L’application enregistre les paramètres utilisateur quand elle s’arrête.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="5b1a9-115">Pour enregistrer les paramètres immédiatement, appelez la méthode `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="5b1a9-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="5b1a9-116">Pour plus d’informations, consultez [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5b1a9-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b1a9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b1a9-117">See also</span></span>

- [<span data-ttu-id="5b1a9-118">My.Settings, objet</span><span class="sxs-lookup"><span data-stu-id="5b1a9-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5b1a9-119">Guide pratique pour lire des paramètres d’application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b1a9-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="5b1a9-120">Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b1a9-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5b1a9-121">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b1a9-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5b1a9-122">Gestion des paramètres d'une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="5b1a9-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
