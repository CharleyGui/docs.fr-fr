---
title: Interprétation du traçage réseau
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: fd617e152b1e86cc71dd8e3cc8a01f1d2f52c30a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047904"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="05d9d-102">Interprétation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="05d9d-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="05d9d-103">Quand le traçage réseau est activé, vous pouvez utiliser cette fonctionnalité pour capturer les appels effectués par votre application aux différents membres de la classe <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="05d9d-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="05d9d-104">La sortie de ces appels peut ressembler aux exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="05d9d-104">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="05d9d-105">Dans l’exemple précédent, [588] est l’identificateur unique du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="05d9d-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="05d9d-106">(4357) et (4387) sont des timestamps qui indiquent le nombre de millisecondes écoulées depuis le démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="05d9d-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="05d9d-107">Les données après les timestamps montrent l’entrée et la sortie de la méthode **Socket.Send** dans l’application.</span><span class="sxs-lookup"><span data-stu-id="05d9d-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="05d9d-108">L’objet qui exécute la méthode **Send** a la valeur 33574638 comme identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="05d9d-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="05d9d-109">La trace de sortie de la méthode inclut la valeur de retour (61 dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="05d9d-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="05d9d-110">Les traces réseau peuvent capturer le trafic réseau qui transite par votre application à l’aide de protocoles de niveau application comme le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="05d9d-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="05d9d-111">Ces données sont capturées au format texte et, éventuellement, au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="05d9d-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="05d9d-112">Les données hexadécimales sont disponibles si vous spécifiez la valeur **includehex** pour l’attribut **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="05d9d-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="05d9d-113">(Pour des informations détaillées sur cet attribut, voir [comment configurer le tracé du réseau](how-to-configure-network-tracing.md).) L’exemple suivant trace a été générée en utilisant **includehex**.</span><span class="sxs-lookup"><span data-stu-id="05d9d-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="05d9d-114">Pour omettre les données hexadécimales, spécifiez la valeur **protocolonly** pour l’attribut **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="05d9d-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="05d9d-115">L’exemple de trace suivant a été généré avec la valeur **protocolonly**.</span><span class="sxs-lookup"><span data-stu-id="05d9d-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="05d9d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05d9d-116">See also</span></span>

- [<span data-ttu-id="05d9d-117">Activation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="05d9d-117">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="05d9d-118">Guide pratique pour configurer le traçage réseau</span><span class="sxs-lookup"><span data-stu-id="05d9d-118">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="05d9d-119">Traçage réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="05d9d-119">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
