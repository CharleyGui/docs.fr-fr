---
title: 'Procédure : lire une valeur à partir d’une clé de Registre'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 74069b111f4316eb81c74f5e62c1fbff6ab8f4b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401847"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="95fd3-102">Guide pratique pour lire une valeur à partir d'une clé de Registre en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95fd3-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="95fd3-103">La méthode `GetValue` de l’objet `My.Computer.Registry` peut être utilisée pour lire les valeurs dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="95fd3-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="95fd3-104">Si la clé « Software\MyApp » de l’exemple suivant n’existe pas, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="95fd3-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="95fd3-105">Si le `ValueName` (« Name » dans l’exemple suivant) n’existe pas, `Nothing` est retourné.</span><span class="sxs-lookup"><span data-stu-id="95fd3-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="95fd3-106">La méthode `GetValue` peut également être utilisée pour déterminer si une valeur donnée existe dans une clé de Registre spécifique.</span><span class="sxs-lookup"><span data-stu-id="95fd3-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="95fd3-107">Lorsque le code lit le contenu du Registre à partir d’une application web, l’utilisateur actuel est déterminé par l’authentification et par l’emprunt d’identité implémenté dans l’application web.</span><span class="sxs-lookup"><span data-stu-id="95fd3-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="95fd3-108">Pour lire une valeur dans une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="95fd3-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="95fd3-109">Utilisez la méthode `GetValue`, en spécifiant un chemin et un nom, pour lire une valeur dans une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="95fd3-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="95fd3-110">L’exemple suivant lit la valeur `Name` dans `HKEY_CURRENT_USER\Software\MyApp` et l’affiche dans la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="95fd3-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="95fd3-111">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="95fd3-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="95fd3-112">Dans le sélecteur d’extraits de code, il se trouve dans **Système d’exploitation Windows > Registre**.</span><span class="sxs-lookup"><span data-stu-id="95fd3-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="95fd3-113">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="95fd3-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="95fd3-114">Pour déterminer si une clé existe dans une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="95fd3-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="95fd3-115">Utilisez la méthode `GetValue` pour récupérer la valeur.</span><span class="sxs-lookup"><span data-stu-id="95fd3-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="95fd3-116">Le code suivant vérifie si la valeur existe et retourne un message si elle n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="95fd3-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="95fd3-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="95fd3-117">Robust Programming</span></span>  

 <span data-ttu-id="95fd3-118">Le Registre contient les clés de niveau supérieur, ou racine, qui sont utilisées pour stocker des données.</span><span class="sxs-lookup"><span data-stu-id="95fd3-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="95fd3-119">Par exemple, la clé racine HKEY_LOCAL_MACHINE est utilisée pour stocker des paramètres d’ordinateur utilisés par tous les utilisateurs, tandis que HKEY_CURRENT_USER est utilisée pour stocker des données spécifiques à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95fd3-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="95fd3-120">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="95fd3-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="95fd3-121">Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="95fd3-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="95fd3-122">L’utilisateur ne dispose pas des autorisations nécessaires pour lire des clés de Registre (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="95fd3-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="95fd3-123">Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="95fd3-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="95fd3-124">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95fd3-124">.NET Framework Security</span></span>  

 <span data-ttu-id="95fd3-125">Pour exécuter ce processus, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="95fd3-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="95fd3-126">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="95fd3-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="95fd3-127">De même, l’utilisateur doit disposer de listes de contrôle d’accès (ACL) valides pour créer ou écrire des paramètres.</span><span class="sxs-lookup"><span data-stu-id="95fd3-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="95fd3-128">Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="95fd3-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="95fd3-129">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="95fd3-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fd3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95fd3-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="95fd3-131">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="95fd3-131">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
