---
title: Liaisons WS-MetadataExchange
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 94f0ba602cd1f58f5491a44a64e24be8ea52895b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293986"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="f480d-102">Liaisons WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="f480d-102">WS-MetadataExchange Bindings</span></span>

<span data-ttu-id="f480d-103">Cette rubrique décrit comment les liaisons d’échange de métadonnées par défaut sont construites pour les divers transports.</span><span class="sxs-lookup"><span data-stu-id="f480d-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="f480d-104">Liaisons par défaut</span><span class="sxs-lookup"><span data-stu-id="f480d-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="f480d-105">Nom de la liaison par défaut</span><span class="sxs-lookup"><span data-stu-id="f480d-105">Default Binding Name</span></span>|<span data-ttu-id="f480d-106">Construction de la liaison</span><span class="sxs-lookup"><span data-stu-id="f480d-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="f480d-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f480d-107">mexHttpBinding</span></span>|<span data-ttu-id="f480d-108"><xref:System.ServiceModel.WSHttpBinding> avec la sécurité au niveau du transport désactivée.</span><span class="sxs-lookup"><span data-stu-id="f480d-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="f480d-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="f480d-109">mexHttpsBinding</span></span>|<span data-ttu-id="f480d-110"><xref:System.ServiceModel.WSHttpBinding> qui prend en charge la sécurité au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="f480d-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="f480d-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="f480d-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="f480d-112"><xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> en utilisant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f480d-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="f480d-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f480d-113">mexTcpBinding</span></span>|<span data-ttu-id="f480d-114"><xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.TcpTransportBindingElement> en utilisant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f480d-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
