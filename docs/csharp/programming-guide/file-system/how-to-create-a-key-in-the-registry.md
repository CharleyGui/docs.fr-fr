---
title: Comment créer une clé dans le registre-Guide de programmation C#
description: Découvrez comment créer une clé dans le registre. Consultez un exemple de code, compilation d’instructions et ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 6db076bc22e098c285b74a8c10e8b5f456c2c55e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299979"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="469e3-104">Comment créer une clé dans le registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="469e3-104">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="469e3-105">Cet exemple ajoute la paire de valeurs « Name » et « Isabella » dans le Registre de l’utilisateur actuel, sous la clé « Names ».</span><span class="sxs-lookup"><span data-stu-id="469e3-105">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="469e3-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="469e3-106">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="469e3-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="469e3-107">Compiling the Code</span></span>  
  
- <span data-ttu-id="469e3-108">Copiez le code et collez-le dans la méthode `Main` d’une application console.</span><span class="sxs-lookup"><span data-stu-id="469e3-108">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="469e3-109">Remplacez le paramètre `Names` par le nom d’une clé qui existe directement sous le nœud HKEY_CURRENT_USER du Registre.</span><span class="sxs-lookup"><span data-stu-id="469e3-109">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="469e3-110">Remplacez le paramètre `Name` par le nom d’une valeur qui existe directement sous le nœud Names.</span><span class="sxs-lookup"><span data-stu-id="469e3-110">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="469e3-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="469e3-111">Robust Programming</span></span>  
 <span data-ttu-id="469e3-112">Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé.</span><span class="sxs-lookup"><span data-stu-id="469e3-112">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="469e3-113">Par exemple, vous souhaiterez peut-être ouvrir la clé Software de l’utilisateur actuel et créer une clé avec le nom de votre société.</span><span class="sxs-lookup"><span data-stu-id="469e3-113">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="469e3-114">Ensuite, ajoutez les valeurs de Registre à la clé de votre société.</span><span class="sxs-lookup"><span data-stu-id="469e3-114">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="469e3-115">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="469e3-115">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="469e3-116">Le nom de la clé est null.</span><span class="sxs-lookup"><span data-stu-id="469e3-116">The name of the key is null.</span></span>  
  
- <span data-ttu-id="469e3-117">L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="469e3-117">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="469e3-118">Le nom de la clé dépasse la limite de 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="469e3-118">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="469e3-119">La clé est fermée.</span><span class="sxs-lookup"><span data-stu-id="469e3-119">The key is closed.</span></span>  
  
- <span data-ttu-id="469e3-120">La clé de Registre est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="469e3-120">The registry key is read-only.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="469e3-121">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="469e3-121">.NET Security</span></span>  
 <span data-ttu-id="469e3-122">Il est plus sûr d’écrire des données dans le dossier utilisateur (`Microsoft.Win32.Registry.CurrentUser`) que sur l’ordinateur local (`Microsoft.Win32.Registry.LocalMachine`).</span><span class="sxs-lookup"><span data-stu-id="469e3-122">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="469e3-123">Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà.</span><span class="sxs-lookup"><span data-stu-id="469e3-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="469e3-124">Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès.</span><span class="sxs-lookup"><span data-stu-id="469e3-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="469e3-125">Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus.</span><span class="sxs-lookup"><span data-stu-id="469e3-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="469e3-126">Pour éviter ce problème, utilisez la méthode `Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="469e3-126">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="469e3-127">.</span><span class="sxs-lookup"><span data-stu-id="469e3-127">method.</span></span> <span data-ttu-id="469e3-128">Elle retourne null si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="469e3-128">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="469e3-129">Il est dangereux de stocker des données confidentielles, telles que des mots de passe, dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="469e3-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469e3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="469e3-130">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="469e3-131">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="469e3-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="469e3-132">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="469e3-132">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="469e3-133">Read, write and delete from the registry with C# (Lire, écrire et supprimer du Registre avec C#)</span><span class="sxs-lookup"><span data-stu-id="469e3-133">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
