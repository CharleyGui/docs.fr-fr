---
title: Référence des classes WMI
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 9830fbf50e8df625e3d3077a66c66e0370204acb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262253"
---
# <a name="wmi-class-reference"></a><span data-ttu-id="dca41-102">Référence des classes WMI</span><span class="sxs-lookup"><span data-stu-id="dca41-102">WMI Class Reference</span></span>

<span data-ttu-id="dca41-103">Cette section répertorie toutes les classes WMI exposées par le fournisseur WMI de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dca41-103">This section lists all the WMI classes exposed by the Windows Communication Foundation (WCF) WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="dca41-104">Accès aux instances WMI</span><span class="sxs-lookup"><span data-stu-id="dca41-104">Accessing WMI Instances</span></span>  

 <span data-ttu-id="dca41-105">Toutes les classes répertoriées dans la référence d'objet WMI ne peuvent pas être directement instanciées, à l'exception de Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation et Endpoint.</span><span class="sxs-lookup"><span data-stu-id="dca41-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="dca41-106">Pour accéder à d'autres instances, vous pouvez accéder aux propriétés des classes de niveau supérieur mentionnées précédemment.</span><span class="sxs-lookup"><span data-stu-id="dca41-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="dca41-107">Par exemple, vous pouvez accéder à l’instance de TransportBindingElement à partir de l’instance de point de terminaison-> Binding-> BindingElements.</span><span class="sxs-lookup"><span data-stu-id="dca41-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dca41-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dca41-108">In This Section</span></span>  

 [<span data-ttu-id="dca41-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="dca41-109">ActivityTransfer</span></span>](activitytransfer.md)  
  
 [<span data-ttu-id="dca41-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="dca41-110">AppDomainInfo</span></span>](appdomaininfo.md)  
  
 [<span data-ttu-id="dca41-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="dca41-111">AspNetCompatibilityRequirementsAttribute</span></span>](aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="dca41-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-112">AsymmetricSecurityBindingElement</span></span>](asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="dca41-113">« Classe de comportement »</span><span class="sxs-lookup"><span data-stu-id="dca41-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="dca41-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-114">BinaryMessageEncodingBindingElement</span></span>](binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="dca41-115">Liaison</span><span class="sxs-lookup"><span data-stu-id="dca41-115">Binding</span></span>](binding.md)  
  
 [<span data-ttu-id="dca41-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-116">BindingElement</span></span>](bindingelement.md)  
  
 [<span data-ttu-id="dca41-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-117">CallbackBehavior</span></span>](callbackbehavior.md)  
  
 [<span data-ttu-id="dca41-118">Channel, classe</span><span class="sxs-lookup"><span data-stu-id="dca41-118">Channel class</span></span>](channel-class.md)  
  
 [<span data-ttu-id="dca41-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dca41-119">ChannelPoolSettings</span></span>](channelpoolsettings.md)  
  
 [<span data-ttu-id="dca41-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="dca41-120">ClientCredentials</span></span>](clientcredentials.md)  
  
 [<span data-ttu-id="dca41-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-121">ClientViaBehavior</span></span>](clientviabehavior.md)  
  
 [<span data-ttu-id="dca41-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-122">CompositeDuplexBindingElement</span></span>](compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="dca41-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-123">ConnectionOrientedTransportBindingElement</span></span>](connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-124">Façon</span><span class="sxs-lookup"><span data-stu-id="dca41-124">Contract</span></span>](contract.md)  
  
 [<span data-ttu-id="dca41-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-125">CustomBindingElement</span></span>](custombindingelement.md)  
  
 [<span data-ttu-id="dca41-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="dca41-126">DeliveryRequirementsAttribute</span></span>](deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="dca41-127">Point de terminaison</span><span class="sxs-lookup"><span data-stu-id="dca41-127">Endpoint</span></span>](endpoint.md)  
  
 [<span data-ttu-id="dca41-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-128">HttpsTransportBindingElement</span></span>](httpstransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-129">HttpTransportBindingElement</span></span>](httptransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="dca41-130">LocalServiceSecuritySettings</span></span>](localservicesecuritysettings.md)  
  
 [<span data-ttu-id="dca41-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-131">MatchAllEndpointBehavior</span></span>](matchallendpointbehavior.md)  
  
 [<span data-ttu-id="dca41-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-132">MessageEncodingBindingElement</span></span>](messageencodingbindingelement.md)  
  
 [<span data-ttu-id="dca41-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="dca41-133">MsmqBindingElementBase</span></span>](msmqbindingelementbase.md)  
  
 [<span data-ttu-id="dca41-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-134">MsmqIntegrationBindingElement</span></span>](msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="dca41-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-135">MsmqTransportBindingElement</span></span>](msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-136">MtomMessageEncodingBindingElement</span></span>](mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="dca41-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-137">MustUnderstandBehavior</span></span>](mustunderstandbehavior.md)  
  
 [<span data-ttu-id="dca41-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dca41-138">NamedPipeConnectionPoolSettings</span></span>](namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="dca41-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-139">NamedPipeTransportBindingElement</span></span>](namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-140">OneWayBindingElement</span></span>](onewaybindingelement.md)  
  
 <span data-ttu-id="dca41-141">« Classe d’opération »</span><span class="sxs-lookup"><span data-stu-id="dca41-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="dca41-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="dca41-142">OperationBehaviorAttribute</span></span>](operationbehaviorattribute.md)  
  
 [<span data-ttu-id="dca41-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-143">PeerCustomResolverBindingElement</span></span>](peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="dca41-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-144">PeerResolverBindingElement</span></span>](peerresolverbindingelement.md)  
  
 [<span data-ttu-id="dca41-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="dca41-145">PeerSecuritySettings</span></span>](peersecuritysettings.md)  
  
 [<span data-ttu-id="dca41-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-146">PeerTransportBindingElement</span></span>](peertransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="dca41-147">PeerTransportSecuritySettings</span></span>](peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="dca41-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-148">PnrpPeerResolverBindingElement</span></span>](pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="dca41-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-149">PrivacyNoticeBindingElement</span></span>](privacynoticebindingelement.md)  
  
 [<span data-ttu-id="dca41-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-150">ReliableSessionBindingElement</span></span>](reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="dca41-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-151">SecurityBindingElement</span></span>](securitybindingelement.md)  
  
 [<span data-ttu-id="dca41-152">Service</span><span class="sxs-lookup"><span data-stu-id="dca41-152">Service</span></span>](service.md)  
  
 [<span data-ttu-id="dca41-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="dca41-153">ServiceAppDomain</span></span>](serviceappdomain.md)  
  
 [<span data-ttu-id="dca41-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-154">ServiceAuthorizationBehavior</span></span>](serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="dca41-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="dca41-155">ServiceBehaviorAttribute</span></span>](servicebehaviorattribute.md)  
  
 [<span data-ttu-id="dca41-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="dca41-156">ServiceCredentials</span></span>](servicecredentials.md)  
  
 [<span data-ttu-id="dca41-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-157">ServiceDebugBehavior</span></span>](servicedebugbehavior.md)  
  
 [<span data-ttu-id="dca41-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-158">ServiceMetadataBehavior</span></span>](servicemetadatabehavior.md)  
  
 [<span data-ttu-id="dca41-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-159">ServiceSecurityAuditBehavior</span></span>](servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="dca41-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-160">ServiceThrottlingBehavior</span></span>](servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="dca41-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-161">ServiceTimeoutsBehavior</span></span>](servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="dca41-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="dca41-162">ServiceToEndpointAssociation</span></span>](servicetoendpointassociation.md)  
  
 [<span data-ttu-id="dca41-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-163">SslStreamSecurityBindingElement</span></span>](sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="dca41-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-164">SymmetricSecurityBindingElement</span></span>](symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="dca41-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-165">SynchronousReceiveBehavior</span></span>](synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="dca41-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dca41-166">TcpConnectionPoolSettings</span></span>](tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="dca41-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-167">TcpTransportBindingElement</span></span>](tcptransportbindingelement.md)  
  
 [<span data-ttu-id="dca41-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-168">TextMessageEncodingBindingElement</span></span>](textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="dca41-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="dca41-169">TraceListener</span></span>](tracelistener.md)  
  
 [<span data-ttu-id="dca41-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="dca41-170">TraceListenerArgument</span></span>](tracelistenerargument.md)  
  
 [<span data-ttu-id="dca41-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-171">TransactedBatchingBehavior</span></span>](transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="dca41-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="dca41-172">TransactionFlowAttribute</span></span>](transactionflowattribute.md)  
  
 [<span data-ttu-id="dca41-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-173">TransactionFlowBindingElement</span></span>](transactionflowbindingelement.md)  
  
 [<span data-ttu-id="dca41-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-174">TransportBindingElement</span></span>](transportbindingelement.md)  
  
 [<span data-ttu-id="dca41-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-175">TransportSecurityBindingElement</span></span>](transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="dca41-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-176">UseManagedPresentationBindingElement</span></span>](usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="dca41-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dca41-177">WindowsStreamSecurityBindingElement</span></span>](windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="dca41-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="dca41-178">WSAT_TraceEvent</span></span>](wsat-traceevent.md)  
  
 [<span data-ttu-id="dca41-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="dca41-179">WSAT_TraceProvider</span></span>](wsat-traceprovider.md)  
  
 [<span data-ttu-id="dca41-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="dca41-180">WSAT_TraceRecord</span></span>](wsat-tracerecord.md)  
  
 [<span data-ttu-id="dca41-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="dca41-181">XmlDictionaryReaderQuotas</span></span>](xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="dca41-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="dca41-182">XmlSerializerOperationBehavior</span></span>](xmlserializeroperationbehavior.md)
