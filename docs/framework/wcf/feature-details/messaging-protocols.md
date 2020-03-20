---
title: Protocoles de messagerie
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: d35cd496db32e1a2886f7ca06e7a3d0964f9c9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184582"
---
# <a name="messaging-protocols"></a><span data-ttu-id="5836e-102">Protocoles de messagerie</span><span class="sxs-lookup"><span data-stu-id="5836e-102">Messaging Protocols</span></span>

<span data-ttu-id="5836e-103">La pile de canaux de la Windows Communication Foundation (WCF) utilise des canaux de codage et de transport pour transformer la représentation interne des messages en format fil et l’envoyer en utilisant un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="5836e-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="5836e-104">Le transport le plus couramment utilisé pour l'interopérabilité des services Web est le HTTP, et les encodages les plus couramment utilisés par les services Web sont SOAP 1.1 basé sur XML, SOAP 1.2 et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="5836e-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="5836e-105">Ce sujet couvre les détails de mise <xref:System.ServiceModel.Channels.HttpTransportBindingElement>en œuvre WCF pour les protocoles suivants utilisés par .</span><span class="sxs-lookup"><span data-stu-id="5836e-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="5836e-106">Spécification/document :</span><span class="sxs-lookup"><span data-stu-id="5836e-106">Specification/document:</span></span>

- [<span data-ttu-id="5836e-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="5836e-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="5836e-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span><span class="sxs-lookup"><span data-stu-id="5836e-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="5836e-109">[SOAP 1.2 HTTP Liaison](https://www.w3.org/TR/soap12-part2) Article 7</span><span class="sxs-lookup"><span data-stu-id="5836e-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="5836e-110">Ce sujet couvre les détails de mise <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> en œuvre WCF pour les protocoles suivants qui et l’emploi.</span><span class="sxs-lookup"><span data-stu-id="5836e-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="5836e-111">Spécification/Document:</span><span class="sxs-lookup"><span data-stu-id="5836e-111">Specification/Document:</span></span>

- [<span data-ttu-id="5836e-112">Xml</span><span class="sxs-lookup"><span data-stu-id="5836e-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="5836e-113">SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="5836e-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="5836e-114">SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="5836e-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="5836e-115">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="5836e-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="5836e-116">W3C Web Services Addressing 1.0 – Éléments principaux</span><span class="sxs-lookup"><span data-stu-id="5836e-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="5836e-117">W3C Web Services Addressing 1.0 – Liaison SOAP</span><span class="sxs-lookup"><span data-stu-id="5836e-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="5836e-118">W3C Web Services Adresse 1.0 - WSDL Binding</span><span class="sxs-lookup"><span data-stu-id="5836e-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="5836e-119">W3C Web Services Addressing 1.0 - Métadonnées</span><span class="sxs-lookup"><span data-stu-id="5836e-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="5836e-120">Liaison WSDL SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="5836e-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="5836e-121">Liaison WSDL SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="5836e-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="5836e-122">Ce sujet couvre les détails de la <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> mise en œuvre de WCF pour les protocoles suivants qui emploient.</span><span class="sxs-lookup"><span data-stu-id="5836e-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="5836e-123">Spécification/document :</span><span class="sxs-lookup"><span data-stu-id="5836e-123">Specification/document:</span></span>

- [<span data-ttu-id="5836e-124">Xop</span><span class="sxs-lookup"><span data-stu-id="5836e-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="5836e-125">Liaison MTOM + SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="5836e-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="5836e-126">Liaison MTOM SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="5836e-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="5836e-127">Assertion de MTOM WS-Policy</span><span class="sxs-lookup"><span data-stu-id="5836e-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="5836e-128">Les espaces de noms XML suivants et les préfixes associés sont utilisés tout au long de ce sujet :</span><span class="sxs-lookup"><span data-stu-id="5836e-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="5836e-129">Préfixe</span><span class="sxs-lookup"><span data-stu-id="5836e-129">Prefix</span></span> | <span data-ttu-id="5836e-130">URI (Uniform Resource Identifier) de l'espace de noms</span><span class="sxs-lookup"><span data-stu-id="5836e-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="5836e-131">s11</span><span class="sxs-lookup"><span data-stu-id="5836e-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="5836e-132">s12</span><span class="sxs-lookup"><span data-stu-id="5836e-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="5836e-133">wsa</span><span class="sxs-lookup"><span data-stu-id="5836e-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="5836e-134">wsam</span><span class="sxs-lookup"><span data-stu-id="5836e-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="5836e-135">wsap</span><span class="sxs-lookup"><span data-stu-id="5836e-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="5836e-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="5836e-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="5836e-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="5836e-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="5836e-138">xop</span><span class="sxs-lookup"><span data-stu-id="5836e-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="5836e-139">xmime</span><span class="sxs-lookup"><span data-stu-id="5836e-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="5836e-140">Dp</span><span class="sxs-lookup"><span data-stu-id="5836e-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="5836e-141">SOAP 1.1 et SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="5836e-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="5836e-142">Enveloppe et modèle de traitement</span><span class="sxs-lookup"><span data-stu-id="5836e-142">Envelope and Processing Model</span></span>
<span data-ttu-id="5836e-143">WCF implémente le traitement des enveloppes SOAP 1.1 suivant le profil de base 1.1 (BP11) et le profil de base 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="5836e-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="5836e-144">Le traitement d'enveloppe SOAP 1.2 est implémenté selon SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="5836e-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="5836e-145">Cette section explique certains choix de mise en œuvre pris par WCF en ce qui concerne BP11 et SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="5836e-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="5836e-146">Traitement obligatoire des en-têtes</span><span class="sxs-lookup"><span data-stu-id="5836e-146">Mandatory Header Processing</span></span>
<span data-ttu-id="5836e-147">WCF suit les règles `mustUnderstand` de traitement des en-têtes marqués décrits dans les spécifications SOAP 1.1 et SOAP 1.2, avec les variations suivantes.</span><span class="sxs-lookup"><span data-stu-id="5836e-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="5836e-148">Un message qui entre dans la pile de canaux WCF est traité par des canaux individuels configurés par des éléments contraignants associés, par exemple, l’encodage des messages texte, la sécurité, la messagerie fiable et les transactions.</span><span class="sxs-lookup"><span data-stu-id="5836e-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="5836e-149">Chaque canal reconnaît les en-têtes de l'espace de noms associé et les marque comme compris.</span><span class="sxs-lookup"><span data-stu-id="5836e-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="5836e-150">Une fois qu'un message entre le répartiteur, le module de formatage de l'opération lit les en-têtes attendus par le contrat de message/opération correspondant et les marque comme compris.</span><span class="sxs-lookup"><span data-stu-id="5836e-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="5836e-151">Ensuite, le répartiteur vérifie si des en-têtes restants ne sont pas compris mais marqués comme `mustUnderstand` et lève une exception.</span><span class="sxs-lookup"><span data-stu-id="5836e-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="5836e-152">Les messages qui contiennent des en-têtes `mustUnderstand` ciblant le destinataire ne sont pas traités par le code de l'application destinataire.</span><span class="sxs-lookup"><span data-stu-id="5836e-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="5836e-153">Un tel traitement par couches permet de séparer les couches d'infrastructure et les couches d'application du nœud SOAP :</span><span class="sxs-lookup"><span data-stu-id="5836e-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="5836e-154">B1111: Les en-têtes qui ne sont pas compris sont détectés après le traitement du message par la pile du canal d’infrastructure WCF, mais avant qu’il ne soit traité par application</span><span class="sxs-lookup"><span data-stu-id="5836e-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="5836e-155">La valeur d'en-tête `mustUnderstand` diffère entre SOAP 1.1 et SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="5836e-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="5836e-156">Basic Profile 1.1 exige que la valeur `mustUnderstand` soit définie sur 0 ou 1 pour les messages SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="5836e-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="5836e-157">SOAP 1.2 accepte les valeurs 0, 1, `false` et `true`, mais recommande d'émettre une représentation canonique de valeurs `xs:boolean` (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="5836e-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="5836e-158">B1112: WCF `mustUnderstand` émet des valeurs 0 et 1 pour les deux VERSIONs SOAP 1.1 et SOAP 1.2 de l’enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="5836e-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="5836e-159">WCF accepte l’espace `xs:boolean` de `mustUnderstand` valeur total de l’en-tête (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="5836e-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="5836e-160">Erreurs SOAP</span><span class="sxs-lookup"><span data-stu-id="5836e-160">SOAP Faults</span></span>
<span data-ttu-id="5836e-161">Ce qui suit est une liste des implémentations de défauts SOAP spécifiques à WCF.</span><span class="sxs-lookup"><span data-stu-id="5836e-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="5836e-162">B2121: WCF retourne les codes de défaut `s11:mustUnderstand`SOAP `s11:Client`1.1 suivants: , et `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="5836e-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="5836e-163">B2122: WCF retourne les codes de défaut `s12:MustUnderstand`SOAP `s12:Sender`1.2 suivants: , , et `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="5836e-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="5836e-164">Liaison HTTP</span><span class="sxs-lookup"><span data-stu-id="5836e-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="5836e-165">Liaison HTTP SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="5836e-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="5836e-166">WCF implémente la liaison SOAP1.1 HTTP suivant la section de spécifications 1.1 du Profil de base 1.1 avec les précisions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5836e-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="5836e-167">B2211 : Le service WCF ne met pas en œuvre la réorientation des demandes HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="5836e-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="5836e-168">B2212 : Les clients de WCF prennent en charge LES cookies HTTP conformément au 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="5836e-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="5836e-169">Liaison HTTP SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="5836e-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="5836e-170">WCF met en œuvre la liaison SOAP 1.2 HTTP telle que décrite dans les spécifications SOAP 1.2-partie 2 (SOAP12Part2) avec les précisions suivantes.</span><span class="sxs-lookup"><span data-stu-id="5836e-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="5836e-171">SOAP 1.2 a introduit un paramètre d'action facultatif pour le type de média `application/soap+xml`.</span><span class="sxs-lookup"><span data-stu-id="5836e-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="5836e-172">Ce paramètre est utile pour optimiser la distribution du message sans que le corps du message SOAP soit analysé lorsque la spécification WS-Addressing n'est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="5836e-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="5836e-173">R2221 : le paramètre d’action `application/soap+xml`, lorsqu’il est présent dans une demande SOAP 1.2, doit correspondre à l’attribut `soapAction` sur l’élément `wsoap12:operation` dans la liaison WSDL correspondante.</span><span class="sxs-lookup"><span data-stu-id="5836e-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="5836e-174">R2222 : le paramètre d'action `application/soap+xml`, lorsqu'il est présent dans un message SOAP 1.2, doit correspondre à `wsa:Action` lorsque la spécification WS-Addressing 2004/08 ou WS-Addressing 1.0 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5836e-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="5836e-175">Lorsque la spécification WS-Addressing est désactivée et qu'une demande entrante ne contient pas de paramètre d'action, l'`Action` du message est considérée comme non spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5836e-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="5836e-176">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="5836e-176">WS-Addressing</span></span>
<span data-ttu-id="5836e-177">WCF implémente 3 versions de WS-Addressing :</span><span class="sxs-lookup"><span data-stu-id="5836e-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="5836e-178">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="5836e-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="5836e-179">W3C Web Services Addressing 1.0 Core (ADDR10-CORE) et liaison SOAP (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="5836e-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="5836e-180">WS-Addressing 1.0 - Métadonnées</span><span class="sxs-lookup"><span data-stu-id="5836e-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="5836e-181">Références de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="5836e-181">Endpoint References</span></span>
<span data-ttu-id="5836e-182">Toutes les versions de WS-Addressing que WCF implémente utilisent des références de point de terminaison pour décrire les points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="5836e-183">Références de point de terminaison et versions de WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="5836e-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="5836e-184">WCF met en œuvre un certain nombre de protocoles `EndpointReference` d’infrastructure qui utilisent WS-Addressing et en particulier l’élément et `W3C.WsAddressing.EndpointReferenceType` la classe (par exemple, WS-ReliableMessaging, WS-SecureConversation, et WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="5836e-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="5836e-185">WCF prend en charge l’utilisation de l’une ou l’autre version de WS-Addressing avec d’autres protocoles d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="5836e-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="5836e-186">Les critères de terminaison WCF prennent en charge une version de WS-Addressing par point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="5836e-187">Pour R3111, l’espace `EndpointReference` nom pour l’élément ou le type utilisé dans les messages échangés avec un point de terminaison WCF doit correspondre à la version de WS-Addressing implémentée par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="5836e-188">Par exemple, si un point de terminaison WCF `AcksTo` implémente WS-ReliableMessaging, l’en-tête retourné par un tel point d’arrivée à l’intérieur `CreateSequenceResponse` utilise la version WS-Addressing que l’élément `EncodingBinding` spécifie pour ce critère d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="5836e-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="5836e-189">Références de point de terminaison et métadonnées</span><span class="sxs-lookup"><span data-stu-id="5836e-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="5836e-190">Plusieurs scénarios nécessitent de communiquer des métadonnées ou une référence aux métadonnées pour un point de terminaison donné.</span><span class="sxs-lookup"><span data-stu-id="5836e-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="5836e-191">B3121 : WCF utilise des mécanismes décrits dans la section 6 de la section 6 de WS-MetadataExchange (MEX) pour inclure les métadonnées pour les références de points de terminaison par valeur ou par référence.</span><span class="sxs-lookup"><span data-stu-id="5836e-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="5836e-192">Considérez un scénario où un service WCF nécessite une authentification à l’aide d’un jeton Markup Language (SAML) d’affirmations de sécurité émis par l’émetteur symbolique à `http://sts.fabrikam123.com`.</span><span class="sxs-lookup"><span data-stu-id="5836e-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="5836e-193">Le critère d’évaluation du WCF `sp:IssuedToken` décrit cette exigence `sp:Issuer` d’authentification en utilisant l’affirmation avec une affirmation imbriquée pointant vers l’émetteur symbolique.</span><span class="sxs-lookup"><span data-stu-id="5836e-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="5836e-194">Les applications clientes qui accèdent à l'assertion `sp:Issuer` doivent savoir comment communiquer avec l'émetteur du jetons du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="5836e-195">Le client a besoin de connaître les métadonnées relatives à l'émetteur de jetons.</span><span class="sxs-lookup"><span data-stu-id="5836e-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="5836e-196">À l’aide des extensions de métadonnées de référence définies dans MEX, WCF fournit une référence aux métadonnées d’émetteurs symboliques.</span><span class="sxs-lookup"><span data-stu-id="5836e-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a><span data-ttu-id="5836e-197">En-têtes d'adressage des messages</span><span class="sxs-lookup"><span data-stu-id="5836e-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="5836e-198">En-têtes de message</span><span class="sxs-lookup"><span data-stu-id="5836e-198">Message Headers</span></span>
<span data-ttu-id="5836e-199">Pour les deux versions WS-Addressing, WCF utilise les `wsa:To`en-têtes `wsa:MessageID`de `wsa:RelatesTo`message suivants comme prescrit par les spécifications , `wsa:ReplyTo`, `wsa:Action`, , , et .</span><span class="sxs-lookup"><span data-stu-id="5836e-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="5836e-200">B3211: Pour toutes les versions WS-Addressing, WCF honore, mais ne produit pas `wsa:FaultTo` hors `wsa:From`de la boîte, WS-Addressing en-têtes de message et .</span><span class="sxs-lookup"><span data-stu-id="5836e-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="5836e-201">Les applications qui interagissent avec les applications WCF peuvent ajouter ces en-têtes de message et WCF les traitera en conséquence.</span><span class="sxs-lookup"><span data-stu-id="5836e-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="5836e-202">Paramètres et propriétés de référence</span><span class="sxs-lookup"><span data-stu-id="5836e-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="5836e-203">WCF met en œuvre le traitement des paramètres de référence des points de terminaison et des propriétés de référence conformément aux spécifications respectives.</span><span class="sxs-lookup"><span data-stu-id="5836e-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="5836e-204">B3221 : Lorsqu’ils sont configurés pour utiliser WS-Addressing 2004/08, les critères de terminaison WCF ne font pas de distinction entre le traitement des propriétés de référence et les paramètres de référence.</span><span class="sxs-lookup"><span data-stu-id="5836e-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="5836e-205">Modèles d’échange de messages</span><span class="sxs-lookup"><span data-stu-id="5836e-205">Message Exchange Patterns</span></span>
<span data-ttu-id="5836e-206">La séquence des messages impliqués dans l’invocation de l’opération de service Web est appelée *le modèle d’échange de messages*.</span><span class="sxs-lookup"><span data-stu-id="5836e-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="5836e-207">WCF prend en charge les modèles d’échange de messages à sens unique, de demande et de duplex.</span><span class="sxs-lookup"><span data-stu-id="5836e-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="5836e-208">Cette section clarifie les exigences WS-Addressing de traitement des messages en fonction du modèle d’échange de messages utilisé.</span><span class="sxs-lookup"><span data-stu-id="5836e-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="5836e-209">Dans cette section, le demandeur envoie le premier message et le répondeur reçoit le premier message.</span><span class="sxs-lookup"><span data-stu-id="5836e-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="5836e-210">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="5836e-210">One-Way Message</span></span>
<span data-ttu-id="5836e-211">Lorsqu’un critère d’évaluation WCF est `Action` configuré pour prendre en charge les messages avec un modèle donné pour suivre un modèle à sens unique, le critère d’évaluation WCF suit les comportements et les exigences suivants.</span><span class="sxs-lookup"><span data-stu-id="5836e-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="5836e-212">Sauf indication contraire, les comportements et les règles s’appliquent pour les deux versions de WS-Addressing prises en charge dans WCF:</span><span class="sxs-lookup"><span data-stu-id="5836e-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="5836e-213">R3311 : le demandeur doit inclure `wsa:To`, `wsa:Action` et les en-têtes pour tous les paramètres de référence spécifiés par la référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="5836e-214">Lorsque WS-Addressing 2004/08 est utilisée et que des [propriétés de référence] sont spécifiées par la référence de point de terminaison, les en-têtes correspondants doivent également être ajoutés au message.</span><span class="sxs-lookup"><span data-stu-id="5836e-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="5836e-215">B3312: le demandeur peut inclure les en-têtes `MessageID`, `ReplyTo` et `FaultTo`.</span><span class="sxs-lookup"><span data-stu-id="5836e-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="5836e-216">L'infrastructure du récepteur les ignorera, et ils seront passés à l'application.</span><span class="sxs-lookup"><span data-stu-id="5836e-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="5836e-217">R3313: lorsque le HTTP est utilisé et qu'aucun message n'est envoyé sur la section de réponse HTTP, le répondeur doit envoyer une réponse HTTP avec un corps vide et un code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="5836e-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="5836e-218">Lorsque le transport HTTP est utilisé et que le contrat d'opération déclare un message unidirectionnel, la réponse HTTP peut encore être utilisée pour envoyer les messages d'infrastructure. Par exemple, la messagerie fiable peut envoyer un message `SequenceAcknowledgement` sur une réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="5836e-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="5836e-219">B3314 : Le répondant du WCF n’envoie pas de message de défaut en réponse à un message à sens unique.</span><span class="sxs-lookup"><span data-stu-id="5836e-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="5836e-220">Demande-réponse</span><span class="sxs-lookup"><span data-stu-id="5836e-220">Request-Reply</span></span>
<span data-ttu-id="5836e-221">Lorsqu’un critère d’évaluation WCF est `Action` configuré pour un message avec un modèle de réponse préalable, le critère de terminaison WCF suit les comportements et les exigences ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5836e-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="5836e-222">Sauf indication contraire, les comportements et les règles s’appliquent pour les deux versions de WS-Addressing prises en charge dans WCF:</span><span class="sxs-lookup"><span data-stu-id="5836e-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="5836e-223">R3321: Le demandeur doit inclure `wsa:To` `wsa:Action`dans `wsa:MessageID`la demande , , et les en-têtes pour tous les paramètres de référence ou les propriétés de référence (ou les deux) spécifiés par la référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="5836e-224">R3322 : lorsque WS-Addressing 2004/08 est utilisée, `ReplyTo` doit également être inclus dans la demande.</span><span class="sxs-lookup"><span data-stu-id="5836e-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="5836e-225">R3323 : Lorsque WS-Addressing 1.0 est utilisé et `ReplyTo` n’est pas présent dans la `http://www.w3.org/2005/08/addressing/anonymous` demande, une référence par défaut avec la propriété [adresse] égale à elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5836e-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="5836e-226">R3324: Le demandeur `wsa:To`doit `wsa:Action`inclure, et `wsa:RelatesTo` les en-têtes dans le message de réponse, ainsi que les `ReplyTo` en-têtes pour tous les paramètres de référence ou les propriétés de référence (ou les deux) spécifiés par la référence de point de terminaison dans la demande.</span><span class="sxs-lookup"><span data-stu-id="5836e-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="5836e-227">Erreurs d'adressage des services Web</span><span class="sxs-lookup"><span data-stu-id="5836e-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="5836e-228">R3411 : WCF produit les défauts suivants définis par WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="5836e-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="5836e-229">Code</span><span class="sxs-lookup"><span data-stu-id="5836e-229">Code</span></span> | <span data-ttu-id="5836e-230">Cause :</span><span class="sxs-lookup"><span data-stu-id="5836e-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="5836e-231">Le message est arrivé avec un `ReplyTo` différent de l'adresse de réponse établie pour ce canal ; il n'y a aucun point de terminaison qui écoute l'adresse spécifiée dans l'en-tête To.</span><span class="sxs-lookup"><span data-stu-id="5836e-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="5836e-232">les canaux de l'infrastructure ou le répartiteur associé au point de terminaison ne reconnaissent pas l'action spécifiée dans l'en-tête `Action`.</span><span class="sxs-lookup"><span data-stu-id="5836e-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="5836e-233">R3412: WCF produit les défauts suivants définis par WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="5836e-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="5836e-234">Code</span><span class="sxs-lookup"><span data-stu-id="5836e-234">Code</span></span> | <span data-ttu-id="5836e-235">Cause :</span><span class="sxs-lookup"><span data-stu-id="5836e-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="5836e-236">Dupliquer `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="5836e-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="5836e-237">Dupliquer `wsa:RelatesTo` `RelationshipType`avec le même .</span><span class="sxs-lookup"><span data-stu-id="5836e-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="5836e-238">L'en-tête d'adressage requis est absent.</span><span class="sxs-lookup"><span data-stu-id="5836e-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="5836e-239">Le message est arrivé avec un `ReplyTo` différent de l'adresse de réponse établie pour ce canal.</span><span class="sxs-lookup"><span data-stu-id="5836e-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="5836e-240">Il n'y a aucun point de terminaison qui écoute l'adresse spécifiée dans l'en-tête To.</span><span class="sxs-lookup"><span data-stu-id="5836e-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="5836e-241">Une action spécifiée dans l'en-tête `Action` n'est pas reconnue par les canaux de l'infrastructure ou le répartiteur associé au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="5836e-242">Le canal RM renvoie cette erreur pour indiquer que le point de terminaison ne traitera pas la séquence suite à l'examen des en-têtes d'adressage du message `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="5836e-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="5836e-243">Le code des tables précédentes correspond à `FaultCode` dans SOAP 1.1 et `SubCode` (avec Code=Expéditeur) dans SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="5836e-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="5836e-244">Liaison WSDL 1.1 et assertions de WS-Policy</span><span class="sxs-lookup"><span data-stu-id="5836e-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="5836e-245">Utilisation recommandée de WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="5836e-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="5836e-246">WCF utilise des affirmations de politique pour indiquer le support de point final pour une version particulière de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="5836e-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="5836e-247">L'assertion de stratégie suivante possède l'objet de stratégie de point de terminaison [WS-PA] et indique que les messages envoyés et reçus depuis le point de terminaison doivent utiliser WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="5836e-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="5836e-248">Cette assertion de stratégie complète la spécification WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="5836e-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="5836e-249">L'assertion de stratégie indique que les messages envoyés/reçus doivent utiliser WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="5836e-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="5836e-250">L'assertion de stratégie suivante possède un objet de stratégie de point de terminaison [WS-PA] et indique que les messages envoyés et reçus depuis le point de terminaison doivent utiliser WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="5836e-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="5836e-251">L'élément `wsaw10:UsingAddressing` est emprunté à [WS-Adressage-WSDL] et est utilisé dans le contexte de WS-Policy conformément à la section 3.1.2 de cette spécification.</span><span class="sxs-lookup"><span data-stu-id="5836e-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="5836e-252">L’utilisation de l’adressage n’altère pas la sémantique des liaisons HTTP WSDL 1.1, SOAP 1.1 et SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="5836e-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="5836e-253">Par exemple, si une réponse est attendue à une demande envoyée à un point de terminaison qui utilise l’adressage et la liaison HTTP WSDL SOAP 1.x, elle doit être envoyée en utilisant la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="5836e-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="5836e-254">Pour les réponses envoyées via HTTP, l'assertion WS-AM est :</span><span class="sxs-lookup"><span data-stu-id="5836e-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="5836e-255">L'assertion de stratégie complète peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="5836e-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="5836e-256">Toutefois, certains modèles d’échange de messages profitent du fait que deux connexions HTTP réciproques indépendantes soient établies entre le demandeur et le répondeur, par exemple dans le cas de messages unidirectionnels non sollicités envoyés par le répondeur.</span><span class="sxs-lookup"><span data-stu-id="5836e-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="5836e-257">WCF offre une fonctionnalité par laquelle deux canaux de transport sous-jacents peuvent former un canal Composite Duplex, où un canal est utilisé pour les messages d’entrée et l’autre est utilisé pour les messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="5836e-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="5836e-258">Dans le cas du transport HTTP, le canal duplex composite fournit deux connexions HTTP réciproques.</span><span class="sxs-lookup"><span data-stu-id="5836e-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="5836e-259">Le demandeur utilise une connexion pour envoyer des messages au répondeur, et le répondeur utilise l'autre pour renvoyer des messages au demandeur.</span><span class="sxs-lookup"><span data-stu-id="5836e-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="5836e-260">Pour les réponses envoyées via des demandes HTTP distinctes, l'assertion WS-AM est :</span><span class="sxs-lookup"><span data-stu-id="5836e-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="5836e-261">L'assertion de stratégie complète peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="5836e-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="5836e-262">Pour utiliser l'assertion suivante, qui possède un objet de stratégie de point de terminaison [WS-PA] sur les points de terminaison qui utilisent des liaisons HTTP WSDL 1.1 SOAP 1.x, il est nécessaire d'utiliser deux connexions HTTP réciproques séparées pour transmettre des messages du demandeur au répondeur et du répondeur au demandeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5836e-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="5836e-263">L’instruction précédente mène aux exigences suivantes pour l’en-tête `wsa:ReplyTo` des messages de demande :</span><span class="sxs-lookup"><span data-stu-id="5836e-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="5836e-264">R3514: Les messages de demande envoyés `ReplyTo` à `[address]` un point `http://www.w3.org/2005/08/addressing/anonymous` de terminaison doivent avoir un en-tête avec la propriété n’est pas `wsap10:UsingAddressing` égal `wsap:UsingAddressing` à `cdp:CompositeDuplex` si le point final utilise un WSDL 1.1 SOAP 1.x HTTP liaison et a une alternative de politique avec un ou une affirmation couplée avec attaché.</span><span class="sxs-lookup"><span data-stu-id="5836e-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="5836e-265">R3515: Les messages de demande envoyés `ReplyTo` à `[address]` un point `http://www.w3.org/2005/08/addressing/anonymous`de terminaison doivent avoir un en-tête avec la propriété égale à , ou ne pas avoir un `ReplyTo` en-tête du tout, si le point final utilise un WSDL 1.1 SOAP 1.x HTTP liaison et a une alternative de politique avec `wsap10:UsingAddressing` affirmation et aucune `cdp:CompositeDuplex` affirmation attachée.</span><span class="sxs-lookup"><span data-stu-id="5836e-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="5836e-266">R3516: Les messages de demande envoyés `ReplyTo` à `[address]` un point `http://www.w3.org/2005/08/addressing/anonymous` de terminaison doivent avoir un en-tête avec une propriété égale à `wsap:UsingAddressing` si le `cdp:CompositeDuplex` point final utilise un WSDL 1.1 SOAP 1.x HTTP liaison et a une alternative de politique avec affirmation et aucune affirmation ci-jointe.</span><span class="sxs-lookup"><span data-stu-id="5836e-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="5836e-267">La spécification WSDL de WS-Addressing tente de décrire des liaisons de protocole semblables en présentant un élément `<wsaw:Anonymous/>` avec trois valeurs textuelles (obligatoire, facultatif et a interdit) pour indiquer des besoins sur l’en-tête `wsa:ReplyTo` (section 3.2).</span><span class="sxs-lookup"><span data-stu-id="5836e-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="5836e-268">Malheureusement, une telle définition d’élément n’est pas particulièrement utilisable comme une assertion dans le contexte de WS-Policy, car il requiert que les extensions spécifiques au domaine prennent en charge l’intersection d’alternatives à l’aide d’un élément de ce type comme une assertion.</span><span class="sxs-lookup"><span data-stu-id="5836e-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="5836e-269">Une telle définition d'élément indique également la valeur de l'en-tête `ReplyTo` par opposition au comportement du point de terminaison sur la transmission, ce qui le rend spécifique au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="5836e-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="5836e-270">Définition d'action</span><span class="sxs-lookup"><span data-stu-id="5836e-270">Action Definition</span></span>
<span data-ttu-id="5836e-271">WS-Addressing 2004/08 définit un attribut `wsa:Action` pour les éléments `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`.</span><span class="sxs-lookup"><span data-stu-id="5836e-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="5836e-272">La liaison WS-Addressing 1.0 WSDL (WS-ADDR10-WSDL) définit un attribut semblable, `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="5836e-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="5836e-273">La seule différence entre les deux réside dans la sémantique du modèle d’action par défaut décrite à la section 3.3.2 de WS-ADDR et à la section 4.4.4 de WS-ADDR10-WSDL, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5836e-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="5836e-274">Il est raisonnable d’avoir deux critères `portType` d’évaluation qui partagent le même (ou le contrat, dans la terminologie WCF) mais en utilisant différentes versions de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="5836e-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="5836e-275">Mais étant donné que cette action est définie par le `portType` et ne doit pas pour les points de terminaison qui implémentent le `portType`, il devient impossible de prendre en charge les deux modèles d’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="5836e-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="5836e-276">Pour résoudre cette controverse, WCF prend `Action` en charge une seule version de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="5836e-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="5836e-277">B3521 : WCF `wsaw10:Action` utilise `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` l’attribut sur des éléments tels que définis `Action` dans WS-ADDR10-WSDL pour déterminer l’URI pour les messages correspondants indépendamment de la version WS-Addressing utilisée par le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5836e-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="5836e-278">Utilisation des références de point de terminaison à l'intérieur d'un port WSDL</span><span class="sxs-lookup"><span data-stu-id="5836e-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="5836e-279">La section 4.1 de WS-ADDR10-WSDL étend l'élément `wsdl:port` de manière à inclure l'élément enfant `<wsa10:EndpointReference…/>` et décrire le point de terminaison en des termes propres à WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="5836e-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="5836e-280">WCF élargit cet utilitaire sur WS-Addressing 2004/08, permettant `<wsa:EndpointReference…/>` `wsdl:port`d’apparaître comme un élément enfant de .</span><span class="sxs-lookup"><span data-stu-id="5836e-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="5836e-281">R3531 : si un point de terminaison possède une alternative de stratégie attachée avec une assertion de la stratégie `<wsaw10:UsingAddressing/>`, l'élément `wsdl:port` correspondant peut contenir un élément enfant `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="5836e-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="5836e-282">R3532 : `wsdl:port` Si un `<wsa10:EndpointReference …/>`élément `wsa10:EndpointReference/wsa10:Address` enfant contient un élément, `@address` la valeur `wsdl:port` / `wsdl:location` de l’élément enfant doit correspondre à la valeur de l’attribut de l’élément frère ou sœur.</span><span class="sxs-lookup"><span data-stu-id="5836e-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="5836e-283">R3533 : si un point de terminaison possède une alternative de stratégie attachée avec une assertion de la stratégie `<wsap:UsingAddressing/>`, l'élément `wsdl:port` correspondant peut contenir un élément enfant `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="5836e-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="5836e-284">R3534 : `wsdl:port` Si un `<wsa:EndpointReference …/>`élément `wsa:EndpointReference/wsa:Address` enfant contient un élément, `@address` la valeur `wsdl:port` / `wsdl:location` de l’élément enfant doit correspondre à la valeur de l’attribut de l’élément frère ou sœur.</span><span class="sxs-lookup"><span data-stu-id="5836e-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="5836e-285">Composition avec WS-Security</span><span class="sxs-lookup"><span data-stu-id="5836e-285">Composition with WS-Security</span></span>
<span data-ttu-id="5836e-286">D'après les sections relatives à la sécurité de WS-ADDR et WS-ADDR10, il est recommandé que tous les en-têtes d'adressage de messages soient signés avec le corps du message afin de les lier.</span><span class="sxs-lookup"><span data-stu-id="5836e-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="5836e-287">Lorsque WS-Security est utilisée pour la protection de l'intégrité des messages, les en-têtes de message WS-Addressing ainsi que les en-têtes résultant des paramètres ou des propriétés de référence (ou les deux) doivent être signés avec le corps du message.</span><span class="sxs-lookup"><span data-stu-id="5836e-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="5836e-288">Exemples</span><span class="sxs-lookup"><span data-stu-id="5836e-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="5836e-289">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="5836e-289">One-Way Message</span></span>
<span data-ttu-id="5836e-290">Dans ce scénario, l'expéditeur envoie un message unidirectionnel au récepteur.</span><span class="sxs-lookup"><span data-stu-id="5836e-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="5836e-291">SOAP 1.2, HTTP 1.1 et W3C WS-Addressing 1.0 sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="5836e-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="5836e-292">Structure du message de demande : les en-têtes de message incluent les éléments `wsa10:To` et `wsa10:Action`.</span><span class="sxs-lookup"><span data-stu-id="5836e-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="5836e-293">Le corps du message inclut un élément `<app:Ping>` spécifique de l'espace de noms de l'application.</span><span class="sxs-lookup"><span data-stu-id="5836e-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="5836e-294">TÊTES HTTP: La destination dans POST correspond `wsa10:To` à l’URI dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="5836e-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="5836e-295">L'en-tête Content-Type a la valeur `application/soap+xml` comme l'exige SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="5836e-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="5836e-296">Les paramètres `charset` et `action` sont inclus.</span><span class="sxs-lookup"><span data-stu-id="5836e-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="5836e-297">Le paramètre `action` de l'en-tête Content-Type correspond à la valeur de l'en-tête de message `wsa10:Action`.</span><span class="sxs-lookup"><span data-stu-id="5836e-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

<span data-ttu-id="5836e-298">Le récepteur répond avec une réponse HTTP vide et l'état 202.</span><span class="sxs-lookup"><span data-stu-id="5836e-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="5836e-299">Exemple de réponse HTTP :</span><span class="sxs-lookup"><span data-stu-id="5836e-299">An example of the HTTP response:</span></span>

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="5836e-300">SOAP MTOM (Message Transmission Optimization Mechanism)</span><span class="sxs-lookup"><span data-stu-id="5836e-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="5836e-301">Cette section décrit les détails de la mise en œuvre du WCF pour le MTOM DE HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="5836e-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="5836e-302">La technologie MTOM est le mécanisme d’encodage des messages SOAP de la même classe que l’encodage texte/XML traditionnel ou l’encodage binaire WCF.</span><span class="sxs-lookup"><span data-stu-id="5836e-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="5836e-303">MTOM inclut ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="5836e-303">MTOM includes the following:</span></span>

- <span data-ttu-id="5836e-304">Un mécanisme d'encodage XML et d'empaquetage décrit par [XOP] qui optimise les éléments d'information XML qui contiennent les données binaires encodées en Base64 dans des parties binaires séparées.</span><span class="sxs-lookup"><span data-stu-id="5836e-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="5836e-305">Encapsulation MIME du package XOP qui sérialise l'ensemble d'informations XML et chaque partie binaire du package XOP dans une partie MIME séparée.</span><span class="sxs-lookup"><span data-stu-id="5836e-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="5836e-306">Encodage XOP MIME appliqué à l'enveloppe SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="5836e-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="5836e-307">Liaison de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="5836e-307">An HTTP transport binding.</span></span>

<span data-ttu-id="5836e-308">Il est possible d’utiliser MTOM avec des transports non-HTTP avec WCF.</span><span class="sxs-lookup"><span data-stu-id="5836e-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="5836e-309">Toutefois, nous nous concentrerons sur le HTTP dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5836e-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="5836e-310">Le format MTOM tire parti d'un grand ensemble de spécifications qui couvrent MTOM lui-même, XOP et MIME.</span><span class="sxs-lookup"><span data-stu-id="5836e-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="5836e-311">La modularité de cet ensemble d’exigences rend quelque peu difficile la reconstruction des spécifications exactes sur le format et le traitement de la sémantique.</span><span class="sxs-lookup"><span data-stu-id="5836e-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="5836e-312">Cette section décrit les exigences de format et de traitement pour la liaison HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="5836e-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="5836e-313">Encodage de message MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="5836e-314">Génération de messages MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-314">Generating MTOM messages</span></span>
<span data-ttu-id="5836e-315">Le [XOP] la section 3.1 décrit le processus de l'encodage XML avec des détails d'élément qui contiennent des valeurs Base64 dans un package XOP abstraitement défini.</span><span class="sxs-lookup"><span data-stu-id="5836e-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="5836e-316">La séquence d'étapes suivante décrit le processus d'encodage spécifique à MTOM :</span><span class="sxs-lookup"><span data-stu-id="5836e-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="5836e-317">Assurez-vous que l’enveloppe SOAP à encoder `[namespace name]` `http://www.w3.org/2004/08/xop/include` ne `[local name]` contient `Include`aucun élément d’information avec un des et un des .</span><span class="sxs-lookup"><span data-stu-id="5836e-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="5836e-318">Créez un package MIME vide.</span><span class="sxs-lookup"><span data-stu-id="5836e-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="5836e-319">Identifiez dans l'ensemble d'informations XML d'origine les éléments à optimiser.</span><span class="sxs-lookup"><span data-stu-id="5836e-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="5836e-320">Pour que les éléments soient optimisés, `[children]` les caractères qui composent l’élément `xs:base64Binary` d’information doivent être sous la forme canonique de (voir XSD-2, 3.2.16 base64Binary) et ne doivent pas contenir de caractères d’espace blanc précédant, en ligne avec ou suivant le contenu non-blanc-espace.</span><span class="sxs-lookup"><span data-stu-id="5836e-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="5836e-321">Créez une enveloppe SOAP XOP qui est une copie de l'enveloppe SOAP d'origine, mais en remplaçant les enfants de chaque élément d'information identifiés à l'étape précédente par un élément d'information `xop:Include` construit comme suit :</span><span class="sxs-lookup"><span data-stu-id="5836e-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="5836e-322">Transformez les caractères remplacés en données binaires en les traitant comme des données encodées en Base64.</span><span class="sxs-lookup"><span data-stu-id="5836e-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="5836e-323">Générez une valeur d’en-tête Content-ID unique qui satisfait aux exigences R3133 et R3134.</span><span class="sxs-lookup"><span data-stu-id="5836e-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="5836e-324">Générez un en-tête MIME Content-Transfer-Encoding avec la valeur binaire.</span><span class="sxs-lookup"><span data-stu-id="5836e-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="5836e-325">Si l'élément d'information qui est optimisé (le [parent] de l'élément d'information `xop:Include` inséré) a un élément d'information d'attribut `xmime:contentType`, générez un en-tête MIME Content-type avec la valeur de l'attribut `xmime:contentType`.</span><span class="sxs-lookup"><span data-stu-id="5836e-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="5836e-326">Générez une nouvelle partie MIME binaire avec le contenu formé par les données binaires décodées des caractères remplacés traités en Base64, l'en-tête Content-ID de l'étape 4b, l'en-tête Content-Transfer-Encoding de l'étape 4c, l'en-tête Content-Type si généré à l'étape 4d.</span><span class="sxs-lookup"><span data-stu-id="5836e-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="5836e-327">Ajoutez un attribut `href` à l'élément `xop:Include` avec la valeur cid : l'uri dérivé de la valeur d'en-tête Content-ID générée à l'étape 4b.</span><span class="sxs-lookup"><span data-stu-id="5836e-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="5836e-328">Retirez les\<caractères d’enveloppement « » et de « > `cid:`», échappez-vous à la chaîne restante et ajoutez le préfixe.</span><span class="sxs-lookup"><span data-stu-id="5836e-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="5836e-329">Le jeu de caractères minimum suivant est requis pour un échappement par RFC1738 et RFC2396.</span><span class="sxs-lookup"><span data-stu-id="5836e-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="5836e-330">D'autres caractères peuvent faire l'objet d'une séquence d'échappement.</span><span class="sxs-lookup"><span data-stu-id="5836e-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="5836e-331">Créez une partie MIME racine avec l'enveloppe SOAP XOP à partir de l'étape 4.</span><span class="sxs-lookup"><span data-stu-id="5836e-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="5836e-332">Écrivez les en-têtes HTTP, y compris l'en-tête HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="5836e-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="5836e-333">Écrivez le package MIME.</span><span class="sxs-lookup"><span data-stu-id="5836e-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="5836e-334">Traitement des messages MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-334">Processing MTOM messages</span></span>
<span data-ttu-id="5836e-335">Le traitement d'un message MTOM est l'inverse exact du processus décrit dans la section précédente « Génération de messages MTOM » :</span><span class="sxs-lookup"><span data-stu-id="5836e-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="5836e-336">Vérifiez que la partie MIME racine possède le `application/xop+xml` Content-type.</span><span class="sxs-lookup"><span data-stu-id="5836e-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="5836e-337">Construisez une enveloppe SOAP en analysant la partie MIME racine du package comme un document XML.</span><span class="sxs-lookup"><span data-stu-id="5836e-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="5836e-338">L'encodage de caractères est déterminé par le paramètre `charset` du Content-type de la partie MIME racine.</span><span class="sxs-lookup"><span data-stu-id="5836e-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="5836e-339">Pour chaque élément d'information dans l'enveloppe SOAP construite, qui a comme seul membre de sa propriété [enfant] un élément d'information `xop:Include` :</span><span class="sxs-lookup"><span data-stu-id="5836e-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="5836e-340">Supprimez le préfixe `cid:` préfixent et annulez toutes les séquences d'échappement d'URI (RFC 2396) dans la valeur de l'attribut `@href` de l'élément `xop:Include`.</span><span class="sxs-lookup"><span data-stu-id="5836e-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="5836e-341">Enfermer la chaîne\<de résultat dans " ", ">".</span><span class="sxs-lookup"><span data-stu-id="5836e-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="5836e-342">Localisez la partie MIME avec la valeur d'en-tête Content-ID qui correspond à la chaîne dérivée à l'étape 3a.</span><span class="sxs-lookup"><span data-stu-id="5836e-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="5836e-343">Remplacez l'élément d'information `xop:Include` qui apparaît dans la propriété `children` de chaque élément par les éléments d'information de caractère qui représentent l'encodage Base64 canonique (voir XSD-2, 3.2.16 base64Binary) du corps d'entité de la partie MIME identifiée à l'étape 3b (remplacez l'élément d'information `xop:Include` par les données reconstruites à partir de la partie du package).</span><span class="sxs-lookup"><span data-stu-id="5836e-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="5836e-344">En-tête HTTP Content-Type</span><span class="sxs-lookup"><span data-stu-id="5836e-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="5836e-345">Ce qui suit est une liste de clarifications WCF pour le format de l’en-tête HTTP Content-Type d’un message SOAP 1.x MTOM-encoded dérivé des exigences énoncées dans la spécification MTOM lui-même et sont dérivés de MTOM et RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="5836e-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="5836e-346">R4131 : un en-tête HTTP Content-Type doit avoir la valeur de multipart/related (non sensible à la casse) et ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="5836e-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="5836e-347">Les noms des paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="5836e-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="5836e-348">L'ordre des paramètres n'est pas important.</span><span class="sxs-lookup"><span data-stu-id="5836e-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="5836e-349">La forme Backus-Naur (BNF) complète de l'en-tête Content-Type pour les messages MIME est répertoriée dans RFC 2045, section 5.1.</span><span class="sxs-lookup"><span data-stu-id="5836e-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="5836e-350">R4132 : un en-tête Content-Type HTTP doit avoir un paramètre de type avec la valeur `application/xop+xml` comprise entre des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="5836e-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="5836e-351">Bien que l’obligation d’utiliser des marques de double citation ne soit pas explicite dans RFC 2387, le\@texte observe que tous les paramètres multipartites/types de médias connexes contiennent très probablement des caractères réservés comme « « ou «/» et ont donc besoin de doubles guillemets.</span><span class="sxs-lookup"><span data-stu-id="5836e-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="5836e-352">R4133 : un en-tête HTTP Content-Type doit avoir un paramètre de début avec la valeur de l'en-tête Content-ID de la partie MIME qui contient l'enveloppe SOAP 1.x, entourée de guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="5836e-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="5836e-353">Si le paramètre de début est omis, la première partie MIME doit contenir l'enveloppe SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="5836e-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="5836e-354">R4134 : un en-tête HTTP Content-Type pour un message SOAP 1.1 encodé en MTOM doit inclure le paramètre start-info avec la valeur de texte/xml, entouré par des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="5836e-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="5836e-355">R4135 : un en-tête Content-Type HTTP pour un message SOAP 1.2 encodé en MTOM doit inclure le paramètre start-info avec la valeur de `application/soap+xml`, entre des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="5836e-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="5836e-356">R4136 : l'en-tête HTTP Content-Type d'un message SOAP 1.x encodé en MTOM doit avoir le paramètre de limite avec la valeur (entourée par des guillemets doubles) qui correspond au BNF de limite MIME défini dans RFC 2046, section 5.1.1</span><span class="sxs-lookup"><span data-stu-id="5836e-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="5836e-357">Exemples :</span><span class="sxs-lookup"><span data-stu-id="5836e-357">Examples:</span></span>

     <span data-ttu-id="5836e-358">CORRECT</span><span class="sxs-lookup"><span data-stu-id="5836e-358">CORRECT</span></span>

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="5836e-359">CORRECT</span><span class="sxs-lookup"><span data-stu-id="5836e-359">CORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="5836e-360">INCORRECT</span><span class="sxs-lookup"><span data-stu-id="5836e-360">INCORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="5836e-361">Partie MIME d'ensemble d'informations</span><span class="sxs-lookup"><span data-stu-id="5836e-361">Infoset MIME Part</span></span>
<span data-ttu-id="5836e-362">L'enveloppe SOAP 1.x est encapsulée comme une partie racine du package MIME XOP et est souvent appelée la partie `infoset`.</span><span class="sxs-lookup"><span data-stu-id="5836e-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="5836e-363">R4141 : l'enveloppe SOAP 1.x doit être encapsulée comme une partie racine du package MIME XOP, appelée la partie `infoset` et référencée depuis le Content-Type HTTP.</span><span class="sxs-lookup"><span data-stu-id="5836e-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="5836e-364">R4142 : la partie SOAP `Infoset` doit inclure les en-têtes MIME suivants : `Content-ID`, `Content-Transfer-Encoding` et `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="5836e-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="5836e-365">Le format de l'en-tête Content-ID est défini par RFC 2045 comme</span><span class="sxs-lookup"><span data-stu-id="5836e-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="5836e-366">où `msg-id` est défini dans RFC 2822 (remplace RFC 822, référencé dans RFC 2045) comme :</span><span class="sxs-lookup"><span data-stu-id="5836e-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="5836e-367">et est effectivement une adresse\<e-mail enfermée dans " et " > ".</span><span class="sxs-lookup"><span data-stu-id="5836e-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="5836e-368">Les préfixe et suffixe `[CFWS]` ont été ajoutés dans RFC 2822 pour contenir des commentaires et ne doivent pas être utilisés pour préserver l'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="5836e-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="5836e-369">R4143 : la valeur de l'en-tête Content-ID pour la partie MIME de l'ensemble d'informations doit suivre la production `msg-id` de RFC 2822 avec les parties `[CFWS]` préfixe et suffixe omises.</span><span class="sxs-lookup"><span data-stu-id="5836e-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="5836e-370">Un certain nombre de implémentations MIME\<assoupli les exigences pour la valeur incluse `absoluteURI` dans "\<et " > " d’être une adresse e-mail et utilisé enfermé dans " , ">" en plus de l’adresse e-mail.</span><span class="sxs-lookup"><span data-stu-id="5836e-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="5836e-371">Cette version de WCF utilise des valeurs de l’en-tête Content-ID MIME du formulaire :</span><span class="sxs-lookup"><span data-stu-id="5836e-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="5836e-372">R4144 : les processeurs MTOM doivent accepter les valeurs d'en-tête Content-ID qui correspondent au `msg-id` assoupli suivant.</span><span class="sxs-lookup"><span data-stu-id="5836e-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="5836e-373">MIME (RFC 2045) fournit l'en-tête Content-Transfer-Encoding pour communiquer l'encodage du contenu de la partie MIME.</span><span class="sxs-lookup"><span data-stu-id="5836e-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="5836e-374">La valeur par défaut définie pour Content-Transfer-Encoding est de 7 bits, ce qui ne convient pas à la plupart des messages SOAP ; l'en-tête Content-Transfer-Encoding est donc nécessaire pour une plus grande interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="5836e-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="5836e-375">R4145 : la partie de l'ensemble d'informations SOAP doit contenir l'en-tête Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="5836e-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="5836e-376">R4146 : si l'encodage de caractères de l'enveloppe SOAP est UTF-8, la valeur de l'en-tête Content-Transfer-Encoding doit être de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="5836e-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="5836e-377">R4147 : si l'encodage de caractères de l'enveloppe SOAP est UTF-16, la valeur de l'en-tête Content-Transfer-Encoding doit être binaire.</span><span class="sxs-lookup"><span data-stu-id="5836e-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="5836e-378">D'après [XOP] section 5,</span><span class="sxs-lookup"><span data-stu-id="5836e-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="5836e-379">R4148: SOAP1.1 La partie Infoset doit contenir l’en-tête content-type avec application de type multimédia/xop xml et paramètres type "texte/xml" et charset</span><span class="sxs-lookup"><span data-stu-id="5836e-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="5836e-380">R4149: La partie SOAP 1.2 Infoset doit contenir `application/xop+xml` l’en-tête`application/soap+xml`Content-Type avec type multimédia et paramètres type " et `charset`.</span><span class="sxs-lookup"><span data-stu-id="5836e-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="5836e-381">Bien que XOP définisse le paramètre `charset` de manière à ce que `application/xop+xml` soit facultatif, il est exigé pour l’interopérabilité comme l’exigence BP 1.1 sur le paramètre `charset` pour le type de média `text/xml`.</span><span class="sxs-lookup"><span data-stu-id="5836e-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="5836e-382">R41410 : Les paramètres `type` et `charset` doivent être présents dans l'en-tête Content-Type de la partie de l'ensemble d'informations SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="5836e-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="5836e-383">Prise en charge des points de terminaison WCF pour MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="5836e-384">L'objectif de MTOM est d'encoder un message SOAP pour optimiser les données encodées en Base64.</span><span class="sxs-lookup"><span data-stu-id="5836e-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="5836e-385">Les contraintes sont répertoriées dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="5836e-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="5836e-386">R4151 : tout élément d'information qui contient des données encodées en Base64 peut être optimisé.</span><span class="sxs-lookup"><span data-stu-id="5836e-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="5836e-387">B4152 : WCF optimise les éléments d’information qui contiennent des données codées de base64 et dépassent 1024 octets de longueur.</span><span class="sxs-lookup"><span data-stu-id="5836e-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="5836e-388">Un point de terminaison WCF configuré pour utiliser MTOM enverra toujours des messages MTOM codés.</span><span class="sxs-lookup"><span data-stu-id="5836e-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="5836e-389">Même si aucune partie ne répond aux critères requis, le message est tout de même encodé en MTOM (sérialisé comme un package MIME avec une partie MIME unique qui contient l'enveloppe SOAP).</span><span class="sxs-lookup"><span data-stu-id="5836e-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="5836e-390">Assertion de WS-Policy pour MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="5836e-391">WCF utilise l’affirmation de politique suivante pour indiquer l’utilisation de MTOM par point de terminaison :</span><span class="sxs-lookup"><span data-stu-id="5836e-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- <span data-ttu-id="5836e-392">R4211 : l'assertion de stratégie précédente a un objet de stratégie de point de terminaison et spécifie que tous les messages envoyés et reçus depuis le point de terminaison doivent être optimisés à l'aide de MTOM.</span><span class="sxs-lookup"><span data-stu-id="5836e-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="5836e-393">B4212 : Lorsqu’il est configuré pour utiliser l’optimisation MTOM, un critère `wsdl:binding`de terminaison WCF ajoute une affirmation de la politique MTOM à la stratégie attachée à la stratégie correspondante .</span><span class="sxs-lookup"><span data-stu-id="5836e-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="5836e-394">Composition avec WS-Security</span><span class="sxs-lookup"><span data-stu-id="5836e-394">Composition with WS-Security</span></span>
<span data-ttu-id="5836e-395">MTOM est un mécanisme d’encodage qui est similaire à `text/xml` WCF Binaire XML.</span><span class="sxs-lookup"><span data-stu-id="5836e-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="5836e-396">MTOM offre la composition naturelle avec WS-Security et d'autre protocoles WS-\* : un message sécurisé à l'aide de WS-Security peut être optimisé à l'aide de MTOM.</span><span class="sxs-lookup"><span data-stu-id="5836e-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="5836e-397">Exemples</span><span class="sxs-lookup"><span data-stu-id="5836e-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="5836e-398">Message SOAP 1.1 WCF encodé à l'aide de MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="5836e-399">Message sécurisé SOAP 1.2 WCF encodé à l'aide de MTOM</span><span class="sxs-lookup"><span data-stu-id="5836e-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="5836e-400">Dans cet exemple, un message est encodé à l'aide de MTOM et SOAP 1.2 et protégé à l'aide de WS-Security.</span><span class="sxs-lookup"><span data-stu-id="5836e-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="5836e-401">Les parties binaires identifiées pour l'encodage sont les contenus du `BinarySecurityToken`, `CipherValue` des `EncryptedData` correspondant à la signature chiffrée et au corps chiffré.</span><span class="sxs-lookup"><span data-stu-id="5836e-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="5836e-402">Notez `CipherValue` que `EncryptedKey` le de la n’a pas été identifié pour l’optimisation par WCF, parce que sa longueur est moins que 1024 octets.</span><span class="sxs-lookup"><span data-stu-id="5836e-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
