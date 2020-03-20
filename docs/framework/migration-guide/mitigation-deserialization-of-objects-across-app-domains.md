---
title: 'Atténuation : désérialisation des objets à travers les domaines d’application'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: e2d90a77cab699646bd31eaa162d1bd1744fd51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457925"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="17663-102">Atténuation : désérialisation des objets à travers les domaines d’application</span><span class="sxs-lookup"><span data-stu-id="17663-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="17663-103">Dans certains cas, lorsqu'une application utilise plusieurs domaines d'application avec différentes bases d'application, la tentative de désérialiser des objets dans le contexte d'appel logique à travers des domaines d'application lève une exception.</span><span class="sxs-lookup"><span data-stu-id="17663-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="17663-104">Diagnostic du problème</span><span class="sxs-lookup"><span data-stu-id="17663-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="17663-105">Le problème survient dans la séquence suivante de conditions :</span><span class="sxs-lookup"><span data-stu-id="17663-105">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="17663-106">Une application utilise deux voire plusieurs domaines d'application avec différentes bases d'application.</span><span class="sxs-lookup"><span data-stu-id="17663-106">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="17663-107">Certains types sont ajoutés explicitement au <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> en appelant une méthode comme <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> ou <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17663-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17663-108">Ces types ne sont pas marqués comme étant sérialisables et ne sont pas inscrits dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="17663-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="17663-109">Ultérieurement, le code, qui s'exécute dans le domaine d'application qui n'est pas le domaine par défaut, essaie de lire une valeur d'un fichier de configuration ou d'utiliser XML pour désérialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="17663-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="17663-110">Afin de lire un fichier de configuration ou de désérialiser l'objet, un objet <xref:System.Xml.XmlReader> essaie d'accéder au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="17663-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="17663-111">Si le système de configuration n'a pas déjà été initialisé, il doit terminer son initialisation.</span><span class="sxs-lookup"><span data-stu-id="17663-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="17663-112">Cela signifie, entre autres, que le runtime doit créer un tracé stable pour le système de configuration, ce qu'il fait comme suit :</span><span class="sxs-lookup"><span data-stu-id="17663-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1. <span data-ttu-id="17663-113">Il recherche une preuve pour le domaine d'application qui n'est pas le domaine par défaut.</span><span class="sxs-lookup"><span data-stu-id="17663-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2. <span data-ttu-id="17663-114">Il essaie de calculer la preuve pour le domaine d'application non défini par défaut, à partir du domaine d'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="17663-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3. <span data-ttu-id="17663-115">L'appel pour obtenir une preuve pour le domaine d'application par défaut déclenche un appel de domaines inter-applications à partir du domaine d'application non défini par défaut vers le domaine d'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="17663-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4. <span data-ttu-id="17663-116">Dans le cadre du contrat de domaines inter-applications du .NET Framework, le contenu du contexte d'appel logique doit être également marshalé à travers les frontières du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="17663-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="17663-117">Parce que les types qui sont dans le contexte d'appel logique ne peuvent pas être résolus dans le domaine d'application par défaut, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="17663-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="17663-118">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="17663-118">Mitigation</span></span>  
 <span data-ttu-id="17663-119">Pour contourner ce problème, procédez comme suit</span><span class="sxs-lookup"><span data-stu-id="17663-119">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="17663-120">Recherchez l'appel à `get_Evidence` dans la pile des appels lorsque l'exception est levée.</span><span class="sxs-lookup"><span data-stu-id="17663-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="17663-121">L'exception peut faire partie d'un grand sous-ensemble d'exceptions, notamment <xref:System.IO.FileNotFoundException> et <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="17663-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="17663-122">Identifiez l'emplacement de l'application dans lequel aucun objet n'est ajouté au contexte d'appel logique et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="17663-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a><span data-ttu-id="17663-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17663-123">See also</span></span>

- [<span data-ttu-id="17663-124">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="17663-124">Application compatibility</span></span>](application-compatibility.md)
