---
title: 'Procédure : référencer les certificats X.509 de façon cohérente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: b5be8990384178c1954834204c23c0b9cf4a5ad9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257273"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="3b4bc-102">Procédure : référencer les certificats X.509 de façon cohérente</span><span class="sxs-lookup"><span data-stu-id="3b4bc-102">How to: Consistently Reference X.509 Certificates</span></span>

<span data-ttu-id="3b4bc-103">Vous pouvez identifier un certificat de plusieurs manières : par le hachage du certificat, par l'émetteur et le numéro de série ou par l'identificateur de la clé du sujet.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="3b4bc-104">L'identificateur de la clé du sujet fournit une identification unique de la clé publique du sujet du certificat et sert souvent dans le cadre des signatures numériques XML.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="3b4bc-105">La valeur du SKI fait généralement partie du certificat X. 509 en tant qu' *extension de certificat x. 509*.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="3b4bc-106">Windows Communication Foundation (WCF) a un *style de référencement* par défaut qui utilise l’émetteur et le numéro de série si l’extension de ski est absente du certificat.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="3b4bc-107">Si le certificat contient l’extension de l’identificateur, le style de référencement utilise par défaut l’identificateur pour pointer vers le certificat.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="3b4bc-108">Si, à travers le développement d’une application, vous passez de certificats qui n’utilisent pas l’extension SKI à des certificats qui utilisent l’extension SKI, le style de référencement utilisé dans les messages générés par WCF change également.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="3b4bc-109">Si un style de référencement cohérent est requis indépendamment de la présence de l'extension de l'identificateur de la clé du sujet, il est possible de configurer ce style de référencement souhaité comme l'illustre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b4bc-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3b4bc-110">Example</span></span>  

 <span data-ttu-id="3b4bc-111">L’exemple suivant crée un élément de liaison de sécurité personnalisé qui utilise un seul style de référencement cohérent, le nom de l’émetteur et le numéro de série.</span><span class="sxs-lookup"><span data-stu-id="3b4bc-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b4bc-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3b4bc-112">Compiling the Code</span></span>  

 <span data-ttu-id="3b4bc-113">Les espaces de noms suivants sont requis pour compiler le code :</span><span class="sxs-lookup"><span data-stu-id="3b4bc-113">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="3b4bc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b4bc-114">See also</span></span>

- [<span data-ttu-id="3b4bc-115">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="3b4bc-115">Working with Certificates</span></span>](working-with-certificates.md)
