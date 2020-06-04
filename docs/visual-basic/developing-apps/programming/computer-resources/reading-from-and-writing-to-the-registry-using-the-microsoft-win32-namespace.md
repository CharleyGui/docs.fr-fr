---
title: Lecture et écriture dans le Registre à l'aide de l'espace de noms Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 10431b1ad40ed320541a22fb46cc8db6dbb775b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360070"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="66c50-102">Lecture et écriture dans le Registre à l'aide de l'espace de noms Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66c50-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="66c50-103">Même si `My.Computer.Registry` doit normalement couvrir vos besoins de base quand vous programmez le Registre, vous pouvez également utiliser les classes <xref:Microsoft.Win32.Registry> et <xref:Microsoft.Win32.RegistryKey> dans l’espace de noms <xref:Microsoft.Win32> du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66c50-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="66c50-104">Clés dans la classe de Registre</span><span class="sxs-lookup"><span data-stu-id="66c50-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="66c50-105">La classe <xref:Microsoft.Win32.Registry> fournit les clés de Registre de base qui peuvent être utilisées pour accéder aux sous-clés et à leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="66c50-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="66c50-106">Les clés de base proprement dites sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="66c50-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="66c50-107">Le tableau suivant répertorie et décrit les sept clés exposées par la classe <xref:Microsoft.Win32.Registry>.</span><span class="sxs-lookup"><span data-stu-id="66c50-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="66c50-108">**Clé**</span><span class="sxs-lookup"><span data-stu-id="66c50-108">**Key**</span></span>|<span data-ttu-id="66c50-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="66c50-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="66c50-110">Définit les types de documents et les propriétés associées à ces types.</span><span class="sxs-lookup"><span data-stu-id="66c50-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="66c50-111">Contient des informations sur la configuration matérielle qui ne sont pas propres à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66c50-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="66c50-112">Contient des informations sur les préférences de l’utilisateur actuel, telles que les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="66c50-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="66c50-113">Contient des données de Registre dynamiques, telles que celles utilisées par les pilotes de périphériques virtuels.</span><span class="sxs-lookup"><span data-stu-id="66c50-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="66c50-114">Contient cinq sous-clés (Hardware, SAM, Security, Software et System) qui contiennent les données de configuration de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="66c50-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="66c50-115">Contient des informations sur les performances des composants logiciels.</span><span class="sxs-lookup"><span data-stu-id="66c50-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="66c50-116">Contient des informations sur les préférences de l’utilisateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="66c50-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="66c50-117">Il est plus sûr d’écrire des données dans l’utilisateur actuel (<xref:Microsoft.Win32.Registry.CurrentUser>) que dans l’ordinateur local (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="66c50-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="66c50-118">Une condition généralement appelée « usurpation » se produit quand la clé que vous créez a été créée précédemment par un autre processus, potentiellement malveillant.</span><span class="sxs-lookup"><span data-stu-id="66c50-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="66c50-119">Pour éviter ce problème, utilisez une méthode, telle que <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, qui retourne `Nothing` si la clé n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="66c50-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="66c50-120">Lecture d’une valeur à partir du Registre</span><span class="sxs-lookup"><span data-stu-id="66c50-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="66c50-121">Le code suivant montre comment lire une chaîne à partir de HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="66c50-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="66c50-122">Le code suivant lit, incrémente puis écrit une chaîne dans HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="66c50-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="66c50-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66c50-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="66c50-124">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="66c50-124">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="66c50-125">Lecture et écriture dans le Registre</span><span class="sxs-lookup"><span data-stu-id="66c50-125">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="66c50-126">Sécurité et Registre</span><span class="sxs-lookup"><span data-stu-id="66c50-126">Security and the Registry</span></span>](security-and-the-registry.md)
