---
title: 'Procédure : lire des paramètres au moment de l’exécution avec C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710229"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="79efd-102">Procédure : Lire les paramètres au moment de l’exécution avec C\#</span><span class="sxs-lookup"><span data-stu-id="79efd-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="79efd-103">Vous pouvez lire les paramètres de portée application et de portée utilisateur au moment de l'exécution via l'objet Propriétés.</span><span class="sxs-lookup"><span data-stu-id="79efd-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="79efd-104">L’objet Properties expose tous les paramètres par défaut du projet via le membre Properties. Settings. default dans l’espace de noms par défaut du projet dans lequel ils sont définis.</span><span class="sxs-lookup"><span data-stu-id="79efd-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="79efd-105">Pour lire les paramètres au moment de l’exécution avec C\#</span><span class="sxs-lookup"><span data-stu-id="79efd-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="79efd-106">Accédez au paramètre approprié via le membre Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="79efd-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="79efd-107">L'exemple suivant montre comment affecter un paramètre nommé `myColor` à une propriété BackColor.</span><span class="sxs-lookup"><span data-stu-id="79efd-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="79efd-108">Au préalable, vous devez avoir créé un fichier de paramètres contenant un paramètre nommé `myColor` de type `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="79efd-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="79efd-109">Pour plus d’informations sur la création d’un [fichier de paramètres, consultez Procédure: Créez un nouveau paramètre au moment](how-to-create-a-new-setting-at-design-time.md)du Design.</span><span class="sxs-lookup"><span data-stu-id="79efd-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="79efd-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79efd-110">See also</span></span>

- [<span data-ttu-id="79efd-111">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="79efd-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="79efd-112">Guide pratique pour Écrire des paramètres utilisateur au moment de l’exécution avecC#</span><span class="sxs-lookup"><span data-stu-id="79efd-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="79efd-113">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="79efd-113">Application Settings Overview</span></span>](application-settings-overview.md)
