---
title: "Comment : écrire des paramètres utilisateur au moment de l'exécution avec C#"
description: Apprenez à écrire des paramètres au moment de l’exécution avec C# en persistance des modifications apportées aux paramètres entre les sessions d’application en appelant la méthode Save.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904323"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="910ec-103">Comment : écrire des paramètres utilisateur au moment de l’exécution avec C\#</span><span class="sxs-lookup"><span data-stu-id="910ec-103">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="910ec-104">Les paramètres de portée application sont en lecture seule et ne peuvent être modifiés qu'au moment du design ou en modifiant le fichier .config entre les sessions d'application.</span><span class="sxs-lookup"><span data-stu-id="910ec-104">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="910ec-105">Les paramètres de portée utilisateur peuvent être écrits au moment de l'exécution tout comme vous modifieriez une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="910ec-105">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="910ec-106">La nouvelle valeur est conservée pendant toute la durée de la session d'application.</span><span class="sxs-lookup"><span data-stu-id="910ec-106">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="910ec-107">Vous pouvez conserver les modifications apportées aux paramètres d'une session d'application à une autre en appelant la méthode Save.</span><span class="sxs-lookup"><span data-stu-id="910ec-107">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="910ec-108">Comment : écrire et conserver des paramètres utilisateur au moment de l’exécution avec C\#</span><span class="sxs-lookup"><span data-stu-id="910ec-108">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="910ec-109">Accédez au paramètre et attribuez-lui une nouvelle valeur comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="910ec-109">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="910ec-110">Si vous souhaitez conserver les modifications apportées aux paramètres d'une session d'application à l'autre, appelez la méthode Save comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="910ec-110">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="910ec-111">Les paramètres utilisateur sont enregistrés dans un fichier dans un sous-dossier du dossier de données d’application masqué local de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="910ec-111">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="910ec-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="910ec-112">See also</span></span>

- [<span data-ttu-id="910ec-113">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="910ec-113">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="910ec-114">Comment : lire des paramètres au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="910ec-114">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="910ec-115">Vue d’ensemble des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="910ec-115">Application Settings Overview</span></span>](application-settings-overview.md)
