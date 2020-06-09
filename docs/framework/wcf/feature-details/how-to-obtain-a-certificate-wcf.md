---
title: 'Comment : obtenir un certificat (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: d020f3e97023d07abb572d30dd53896bfec1da46
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597018"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="17c84-102">Comment : obtenir un certificat (WCF)</span><span class="sxs-lookup"><span data-stu-id="17c84-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="17c84-103">Pour utiliser l’une des fonctionnalités de Windows Communication Foundation (WCF) de qui utilisent des certificats X. 509, vous devez tout d’abord obtenir des certificats.</span><span class="sxs-lookup"><span data-stu-id="17c84-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="17c84-104">Pour obtenir un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="17c84-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="17c84-105">Choisissez l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="17c84-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="17c84-106">Achetez un certificat auprès d'une autorité de certification, telle que VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="17c84-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="17c84-107">Installez votre propre service de certificats et faites en sorte qu'une autorité de certification signe les certificats.</span><span class="sxs-lookup"><span data-stu-id="17c84-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="17c84-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter et Windows 2000 Datacenter Server incluent tous les services de certificats qui prennent en charge l’infrastructure de clé publique (PKI).</span><span class="sxs-lookup"><span data-stu-id="17c84-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="17c84-109">Dans Windows Server 2008, utilisez le rôle [services de certificats Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) pour gérer une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="17c84-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="17c84-110">Installez votre propre service de certificats et ne faites pas signer les certificats.</span><span class="sxs-lookup"><span data-stu-id="17c84-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="17c84-111">Quelle que soit la méthode adoptée, le destinataire de la demande SOAP contenant le certificat X.509 doit approuver ce dernier.</span><span class="sxs-lookup"><span data-stu-id="17c84-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="17c84-112">Cela signifie que le certificat X.509 ou un émetteur dans la chaîne de certificats se trouve dans le magasin de certificats Personnes de confiance et que le certificat X.509 ne se trouve pas dans le magasin de certificats non fiables.</span><span class="sxs-lookup"><span data-stu-id="17c84-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c84-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17c84-113">See also</span></span>

- [<span data-ttu-id="17c84-114">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="17c84-114">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="17c84-115">Guide pratique pour créer des certificats temporaires à utiliser au cours du développement</span><span class="sxs-lookup"><span data-stu-id="17c84-115">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
