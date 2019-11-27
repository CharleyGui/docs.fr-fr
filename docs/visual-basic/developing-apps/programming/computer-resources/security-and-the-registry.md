---
title: Sécurité et Registre
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345486"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="79e3e-102">Sécurité et Registre (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79e3e-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="79e3e-103">Cette page décrit les implications en matière de sécurité du stockage des données dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="79e3e-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="79e3e-104">Autorisations</span><span class="sxs-lookup"><span data-stu-id="79e3e-104">Permissions</span></span>  

 <span data-ttu-id="79e3e-105">Il est dangereux de stocker des données confidentielles (comme des mots de passe) dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="79e3e-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="79e3e-106">L’utilisation du Registre peut compromettre la sécurité en accordant un accès inapproprié à des ressources système ou à des informations protégées.</span><span class="sxs-lookup"><span data-stu-id="79e3e-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="79e3e-107">Pour utiliser ces propriétés, vous devez disposer des autorisations de lecture et d’écriture de l’énumération <xref:System.Security.Permissions.RegistryPermissionAccess>, qui contrôle l’accès aux variables de Registre.</span><span class="sxs-lookup"><span data-stu-id="79e3e-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="79e3e-108">Tout code s’exécutant avec une confiance totale (sous la stratégie de sécurité par défaut, il s’agit de n’importe quel code installé sur le disque dur local de l’utilisateur) dispose des autorisations nécessaires pour accéder au Registre.</span><span class="sxs-lookup"><span data-stu-id="79e3e-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="79e3e-109">Pour plus d’informations, consultez la classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="79e3e-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="79e3e-110">Les variables de Registre ne doivent pas être stockées dans des emplacements de mémoire où du code sans <xref:System.Security.Permissions.RegistryPermission> peut y accéder.</span><span class="sxs-lookup"><span data-stu-id="79e3e-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="79e3e-111">De même, quand vous accordez des autorisations, accordez les privilèges minimaux nécessaires pour effectuer la tâche.</span><span class="sxs-lookup"><span data-stu-id="79e3e-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="79e3e-112">Les valeurs des autorisations d’accès au Registre sont définies par l’énumération <xref:System.Security.Permissions.RegistryPermissionAccess>.</span><span class="sxs-lookup"><span data-stu-id="79e3e-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="79e3e-113">Le tableau suivant détaille ses membres.</span><span class="sxs-lookup"><span data-stu-id="79e3e-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="79e3e-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="79e3e-114">Value</span></span>|<span data-ttu-id="79e3e-115">Accès aux variables de Registre</span><span class="sxs-lookup"><span data-stu-id="79e3e-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="79e3e-116">Créer, lire et écrire</span><span class="sxs-lookup"><span data-stu-id="79e3e-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="79e3e-117">Créer</span><span class="sxs-lookup"><span data-stu-id="79e3e-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="79e3e-118">Aucun accès</span><span class="sxs-lookup"><span data-stu-id="79e3e-118">No access</span></span>|  
|`Read`|<span data-ttu-id="79e3e-119">Lecture</span><span class="sxs-lookup"><span data-stu-id="79e3e-119">Read</span></span>|  
|`Write`|<span data-ttu-id="79e3e-120">Écriture</span><span class="sxs-lookup"><span data-stu-id="79e3e-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="79e3e-121">Vérification des valeurs dans les clés de Registre</span><span class="sxs-lookup"><span data-stu-id="79e3e-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="79e3e-122">Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà.</span><span class="sxs-lookup"><span data-stu-id="79e3e-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="79e3e-123">Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès.</span><span class="sxs-lookup"><span data-stu-id="79e3e-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="79e3e-124">Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus.</span><span class="sxs-lookup"><span data-stu-id="79e3e-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="79e3e-125">Pour l’éviter, utilisez la méthode `GetValue`.</span><span class="sxs-lookup"><span data-stu-id="79e3e-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="79e3e-126">Elle retourne `Nothing` si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="79e3e-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="79e3e-127">Lors de la lecture du Registre à partir d’une application web, l’identité de l’utilisateur actuel dépend de l’authentification et de l’emprunt d’identité implémentés dans l’application web.</span><span class="sxs-lookup"><span data-stu-id="79e3e-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e3e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79e3e-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="79e3e-129">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="79e3e-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
