---
title: 'Comment : supprimer une clé de Registre'
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345654"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="d3198-102">Guide pratique pour supprimer une clé de Registre en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3198-102">How to: Delete a Registry Key in Visual Basic</span></span>

<span data-ttu-id="d3198-103">Vous pouvez utiliser les méthodes<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> et <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> pour supprimer les clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="d3198-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d3198-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="d3198-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="d3198-105">Pour supprimer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="d3198-105">To delete a registry key</span></span>  
  
- <span data-ttu-id="d3198-106">Utilisez la méthode `DeleteSubKey` pour supprimer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="d3198-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="d3198-107">Cet exemple supprime la clé Software/TestApp dans la ruche CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="d3198-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="d3198-108">Vous pouvez spécifier la chaîne appropriée dans le code ou faire en sorte que celui-ci repose sur des informations fournies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3198-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d3198-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d3198-109">Robust Programming</span></span>  

 <span data-ttu-id="d3198-110">La méthode `DeleteSubKey` retourne une chaîne vide si la paire clé/valeur n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d3198-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="d3198-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="d3198-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d3198-112">Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d3198-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d3198-113">L’utilisateur ne dispose pas des autorisations pour supprimer des clés de Registre (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d3198-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d3198-114">Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d3198-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d3198-115">La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d3198-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d3198-116">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d3198-116">.NET Framework Security</span></span>  

 <span data-ttu-id="d3198-117">Les appels au Registre échouent quand l’utilisateur ne dispose pas des autorisations d’exécution nécessaires (<xref:System.Security.Permissions.RegistryPermission>) ou de l’accès correct (tel que déterminé par les listes de contrôle d’accès) pour créer ou écrire des paramètres.</span><span class="sxs-lookup"><span data-stu-id="d3198-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="d3198-118">Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d3198-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3198-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3198-119">See also</span></span>

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="d3198-120">Sécurité et Registre</span><span class="sxs-lookup"><span data-stu-id="d3198-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="d3198-121">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="d3198-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
