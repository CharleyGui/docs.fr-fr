---
title: Ajouter une référence de service à un projet de sous-ensemble portable
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: e9a0d3fbc75a8c64af892f74acedfc41dc115da3
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687712"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="8ec05-102">Ajouter une référence de service à un projet de sous-ensemble portable</span><span class="sxs-lookup"><span data-stu-id="8ec05-102">Add Service Reference in a Portable Subset Project</span></span>

<span data-ttu-id="8ec05-103">Les projets de sous-ensemble portables permettent aux programmeurs d’assembly .NET de maintenir une arborescence source unique et le système de génération tout en prenant en charge plusieurs implémentations .NET (Desktop, Silverlight, Windows Phone et Xbox).</span><span class="sxs-lookup"><span data-stu-id="8ec05-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and Xbox).</span></span> <span data-ttu-id="8ec05-104">Les projets de sous-ensemble portables référencent uniquement les bibliothèques portables qui sont des assemblys .NET qui peuvent être utilisés sur n’importe quelle implémentation .NET.</span><span class="sxs-lookup"><span data-stu-id="8ec05-104">Portable subset projects only reference portable libraries that are .NET assemblies that can be used on any .NET implementation.</span></span>
  
## <a name="add-service-reference-details"></a><span data-ttu-id="8ec05-105">Ajouter des détails de référence de service</span><span class="sxs-lookup"><span data-stu-id="8ec05-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="8ec05-106">Lors de l'ajout d'une référence de service dans un projet de sous-ensemble portable, les restrictions suivantes sont appliquées :</span><span class="sxs-lookup"><span data-stu-id="8ec05-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="8ec05-107">Pour <xref:System.Xml.Serialization.XmlSerializer>, seuls les encodages littéraux sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8ec05-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="8ec05-108">Les encodages SOAP génèrent une erreur lors de l'importation.</span><span class="sxs-lookup"><span data-stu-id="8ec05-108">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="8ec05-109">Pour les services qui utilisent des scénarios <xref:System.Runtime.Serialization.DataContractSerializer>, un substitut de contrat de données est fourni pour garantir que les types réutilisés proviennent uniquement du sous-ensemble portable.</span><span class="sxs-lookup"><span data-stu-id="8ec05-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="8ec05-110">Les points de terminaison qui reposent sur des liaisons non prises en charge dans les bibliothèques portables (toutes les liaisons sauf <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> sans flux de transaction, sessions fiables ou encodage MTOM et liaisons personnalisées équivalentes) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="8ec05-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="8ec05-111">Les en-têtes de messages sont supprimés de toutes les descriptions des messages dans toutes les opérations avant importation.</span><span class="sxs-lookup"><span data-stu-id="8ec05-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="8ec05-112">Les attributs non portables <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute> et <xref:System.ServiceModel.TransactionFlowAttribute> sont supprimés du code du proxy client généré.</span><span class="sxs-lookup"><span data-stu-id="8ec05-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="8ec05-113">Les propriétés non portables ProtectionLevel, SessionMode, IsInitiating, IsTerminating sont supprimées de <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute> et <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ec05-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="8ec05-114">Toutes les opérations de service sont générées comme des opérations asynchrones sur le proxy client.</span><span class="sxs-lookup"><span data-stu-id="8ec05-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="8ec05-115">Les constructeurs clients générés qui utilisent des types non portables sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="8ec05-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="8ec05-116">Une instance <xref:System.Net.CookieContainer> est exposée sur le client généré.</span><span class="sxs-lookup"><span data-stu-id="8ec05-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="8ec05-117">Un commentaire est inséré au début du fichier identifiant l'assembly et la version du générateur de code :`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="8ec05-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="8ec05-118">L'interface <xref:System.Runtime.Serialization.ISerializable> n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8ec05-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="8ec05-119">Les liaisons Net.Tcp et PollingDuplex ne sont pas prises en charge</span><span class="sxs-lookup"><span data-stu-id="8ec05-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="8ec05-120"><xref:System.Runtime.Serialization.DataContractSerializer> sera toujours utilisé pour les erreurs.</span><span class="sxs-lookup"><span data-stu-id="8ec05-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="8ec05-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> n'est pas pris en charge dans les projets portables du sous-ensemble.</span><span class="sxs-lookup"><span data-stu-id="8ec05-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec05-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ec05-122">See also</span></span>

- [<span data-ttu-id="8ec05-123">Accès aux services à l'aide d'un client WCF</span><span class="sxs-lookup"><span data-stu-id="8ec05-123">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="8ec05-124">Bibliothèque de classes portable</span><span class="sxs-lookup"><span data-stu-id="8ec05-124">Portable Class Library</span></span>](../cross-platform/portable-class-library.md)
