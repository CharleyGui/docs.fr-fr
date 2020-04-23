---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: bfa7bcefff45bc325d7bba3aa2b9b3a8f0d439fa
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071933"
---
<span data-ttu-id="3fdf3-101">Créez un fichier texte nommé `azureauth.json`.</span><span class="sxs-lookup"><span data-stu-id="3fdf3-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="3fdf3-102">Collez la sortie JSON obtenue à la création du principal de service.</span><span class="sxs-lookup"><span data-stu-id="3fdf3-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="3fdf3-103">Enregistrez ce fichier dans un emplacement sécurisé sur votre système que votre code peut lire.</span><span class="sxs-lookup"><span data-stu-id="3fdf3-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="3fdf3-104">Utilisez PowerShell pour définir une variable d’environnement nommée `AZURE_AUTH_LOCATION` avec le chemin d’accès complet au fichier, par exemple :</span><span class="sxs-lookup"><span data-stu-id="3fdf3-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
