---
title: Comment créer une clé dans le registre - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635442"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="71e5e-102">Comment créer une clé dans le registre (Guide de programmation de CMD)</span><span class="sxs-lookup"><span data-stu-id="71e5e-102">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="71e5e-103">Cet exemple ajoute la paire de valeurs « Name » et « Isabella » dans le Registre de l’utilisateur actuel, sous la clé « Names ».</span><span class="sxs-lookup"><span data-stu-id="71e5e-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="71e5e-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="71e5e-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71e5e-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="71e5e-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="71e5e-106">Copiez le code et collez-le dans la méthode `Main` d’une application console.</span><span class="sxs-lookup"><span data-stu-id="71e5e-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="71e5e-107">Remplacez le paramètre `Names` par le nom d’une clé qui existe directement sous le nœud HKEY_CURRENT_USER du Registre.</span><span class="sxs-lookup"><span data-stu-id="71e5e-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="71e5e-108">Remplacez le paramètre `Name` par le nom d’une valeur qui existe directement sous le nœud Names.</span><span class="sxs-lookup"><span data-stu-id="71e5e-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="71e5e-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="71e5e-109">Robust Programming</span></span>  
 <span data-ttu-id="71e5e-110">Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé.</span><span class="sxs-lookup"><span data-stu-id="71e5e-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="71e5e-111">Par exemple, vous souhaiterez peut-être ouvrir la clé Software de l’utilisateur actuel et créer une clé avec le nom de votre société.</span><span class="sxs-lookup"><span data-stu-id="71e5e-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="71e5e-112">Ensuite, ajoutez les valeurs de Registre à la clé de votre société.</span><span class="sxs-lookup"><span data-stu-id="71e5e-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="71e5e-113">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="71e5e-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="71e5e-114">Le nom de la clé est null.</span><span class="sxs-lookup"><span data-stu-id="71e5e-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="71e5e-115">L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="71e5e-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="71e5e-116">Le nom de la clé dépasse la limite de 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="71e5e-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="71e5e-117">La clé est fermée.</span><span class="sxs-lookup"><span data-stu-id="71e5e-117">The key is closed.</span></span>  
  
- <span data-ttu-id="71e5e-118">La clé de Registre est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="71e5e-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="71e5e-119">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="71e5e-119">.NET Framework Security</span></span>  
 <span data-ttu-id="71e5e-120">Il est plus sûr d’écrire des données dans le dossier utilisateur (`Microsoft.Win32.Registry.CurrentUser`) que sur l’ordinateur local (`Microsoft.Win32.Registry.LocalMachine`).</span><span class="sxs-lookup"><span data-stu-id="71e5e-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="71e5e-121">Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà.</span><span class="sxs-lookup"><span data-stu-id="71e5e-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="71e5e-122">Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès.</span><span class="sxs-lookup"><span data-stu-id="71e5e-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="71e5e-123">Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus.</span><span class="sxs-lookup"><span data-stu-id="71e5e-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="71e5e-124">Pour éviter ce problème, utilisez la méthode `Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="71e5e-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="71e5e-125">.</span><span class="sxs-lookup"><span data-stu-id="71e5e-125">method.</span></span> <span data-ttu-id="71e5e-126">Elle retourne null si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="71e5e-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="71e5e-127">Il est dangereux de stocker des données confidentielles, telles que des mots de passe, dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="71e5e-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e5e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71e5e-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="71e5e-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="71e5e-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="71e5e-130">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="71e5e-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="71e5e-131">Read, write and delete from the registry with C# (Lire, écrire et supprimer du Registre avec C#)</span><span class="sxs-lookup"><span data-stu-id="71e5e-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
