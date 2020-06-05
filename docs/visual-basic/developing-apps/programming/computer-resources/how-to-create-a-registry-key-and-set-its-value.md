---
title: 'Procédure : créer une clé de Registre et définir sa valeur'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: b51a14e5e9c69078330f5b2161f74cff8e4da332
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363446"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="2e730-102">Guide pratique pour créer une clé de Registre et définir sa valeur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e730-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="2e730-103">Vous pouvez utiliser la méthode `CreateSubKey` de l’objet `My.Computer.Registry` pour créer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="2e730-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="2e730-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="2e730-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="2e730-105">Pour créer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="2e730-105">To create a registry key</span></span>

- <span data-ttu-id="2e730-106">Utilisez la méthode `CreateSubKey`, en spécifiant le nom de la clé et sous quelle ruche la placer.</span><span class="sxs-lookup"><span data-stu-id="2e730-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="2e730-107">Le paramètre `Subkey` ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="2e730-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="2e730-108">Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2e730-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="2e730-109">Pour créer une clé de Registre et définir sa valeur</span><span class="sxs-lookup"><span data-stu-id="2e730-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="2e730-110">Utilisez la méthode `CreateSubkey`, en spécifiant le nom de la clé et sous quelle ruche la placer.</span><span class="sxs-lookup"><span data-stu-id="2e730-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="2e730-111">Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2e730-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="2e730-112">Définissez la valeur avec la méthode `SetValue`.</span><span class="sxs-lookup"><span data-stu-id="2e730-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="2e730-113">Cet exemple définit « This is a test value »</span><span class="sxs-lookup"><span data-stu-id="2e730-113">This example sets the string value.</span></span> <span data-ttu-id="2e730-114">comme valeur de chaîne « MyTestKeyValue ».</span><span class="sxs-lookup"><span data-stu-id="2e730-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="2e730-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e730-115">Example</span></span>

<span data-ttu-id="2e730-116">Cet exemple crée la clé de Registre `MyTestKey` sous HKEY_CURRENT_USER, puis affecte `This is a test value` comme valeur de chaîne `MyTestKeyValue`.</span><span class="sxs-lookup"><span data-stu-id="2e730-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="2e730-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="2e730-117">Robust Programming</span></span>

<span data-ttu-id="2e730-118">Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé.</span><span class="sxs-lookup"><span data-stu-id="2e730-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="2e730-119">Par exemple, vous souhaiterez peut-être ouvrir la clé HKEY_CURRENT_USER\Software de l’utilisateur actuel et créer une clé avec le nom de votre société.</span><span class="sxs-lookup"><span data-stu-id="2e730-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="2e730-120">Ensuite, ajoutez les valeurs de Registre à la clé de votre société.</span><span class="sxs-lookup"><span data-stu-id="2e730-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="2e730-121">Lors de la lecture du Registre à partir d’une application web, l’utilisateur actuel dépend de l’authentification et de l’emprunt d’identité implémenté dans l’application web.</span><span class="sxs-lookup"><span data-stu-id="2e730-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="2e730-122">Il est plus sûr d’écrire des données dans le dossier utilisateur (<xref:Microsoft.Win32.Registry.CurrentUser>) que sur l’ordinateur local (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="2e730-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="2e730-123">Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà.</span><span class="sxs-lookup"><span data-stu-id="2e730-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="2e730-124">Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès.</span><span class="sxs-lookup"><span data-stu-id="2e730-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="2e730-125">Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus.</span><span class="sxs-lookup"><span data-stu-id="2e730-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="2e730-126">Pour l’éviter, utilisez la méthode <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e730-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="2e730-127">Elle retourne `Nothing` si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="2e730-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="2e730-128">Il est dangereux de stocker des données confidentielles (telles que des mots de passe) dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="2e730-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="2e730-129">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="2e730-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="2e730-130">Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="2e730-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="2e730-131">L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="2e730-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="2e730-132">Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2e730-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="2e730-133">La clé est fermée (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2e730-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="2e730-134">La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="2e730-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="2e730-135">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e730-135">.NET Framework Security</span></span>

<span data-ttu-id="2e730-136">Pour exécuter ce processus, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="2e730-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="2e730-137">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="2e730-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="2e730-138">De même, l’utilisateur doit disposer de listes de contrôle d’accès (ACL) valides pour créer ou écrire des paramètres.</span><span class="sxs-lookup"><span data-stu-id="2e730-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="2e730-139">Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="2e730-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="2e730-140">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2e730-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e730-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e730-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="2e730-142">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="2e730-142">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="2e730-143">Notions fondamentales de la sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="2e730-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
