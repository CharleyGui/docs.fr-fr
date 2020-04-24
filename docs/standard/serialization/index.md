---
title: Sérialisation-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053345"
---
# <a name="serialization-in-net"></a><span data-ttu-id="bddb6-102">Sérialisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="bddb6-102">Serialization in .NET</span></span>

<span data-ttu-id="bddb6-103">La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable.</span><span class="sxs-lookup"><span data-stu-id="bddb6-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="bddb6-104">Le complément de la sérialisation est la désérialisation, qui convertit un flux de données en un objet.</span><span class="sxs-lookup"><span data-stu-id="bddb6-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="bddb6-105">Ensemble, ces processus autorisent le stockage et le transfert des données.</span><span class="sxs-lookup"><span data-stu-id="bddb6-105">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="bddb6-106">.NET propose les technologies de sérialisation suivantes :</span><span class="sxs-lookup"><span data-stu-id="bddb6-106">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="bddb6-107">[La sérialisation binaire](binary-serialization.md) préserve la fidélité du type, ce qui est utile pour conserver l’état d’un objet entre différents appels d’une application.</span><span class="sxs-lookup"><span data-stu-id="bddb6-107">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="bddb6-108">Par exemple, vous pouvez partager un objet entre plusieurs applications en le sérialisant dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="bddb6-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="bddb6-109">Vous pouvez sérialiser un objet vers un flux, un disque, la mémoire, le réseau, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="bddb6-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="bddb6-110">La communication à distance utilise la sérialisation pour passer des objets « par valeur » d'un ordinateur ou d'un domaine d'application à un autre.</span><span class="sxs-lookup"><span data-stu-id="bddb6-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="bddb6-111">[La sérialisation XML et SOAP](xml-and-soap-serialization.md) sérialise uniquement les propriétés et les champs publics et ne conserve pas la fidélité du type.</span><span class="sxs-lookup"><span data-stu-id="bddb6-111">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="bddb6-112">Ceci est utile lorsque vous souhaitez fournir ou consommer des données sans restreindre l'application qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="bddb6-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="bddb6-113">XML étant une norme ouverte, elle constitue une option intéressante pour partager des données via le Web.</span><span class="sxs-lookup"><span data-stu-id="bddb6-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="bddb6-114">Le protocole SOAP est également une norme ouverte et représente par conséquent une option avantageuse.</span><span class="sxs-lookup"><span data-stu-id="bddb6-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="bddb6-115">[La sérialisation JSON](system-text-json-overview.md) sérialise uniquement les propriétés publiques et ne conserve pas la fidélité du type.</span><span class="sxs-lookup"><span data-stu-id="bddb6-115">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="bddb6-116">JSON est une norme ouverte qui est un choix attrayant pour le partage de données sur le Web.</span><span class="sxs-lookup"><span data-stu-id="bddb6-116">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="bddb6-117">Référence</span><span class="sxs-lookup"><span data-stu-id="bddb6-117">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="bddb6-118">Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.</span><span class="sxs-lookup"><span data-stu-id="bddb6-118">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="bddb6-119">Contient des classes qui peuvent être utilisées pour sérialiser des objets en documents ou en flux de données au format XML.</span><span class="sxs-lookup"><span data-stu-id="bddb6-119">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="bddb6-120">Contient des classes qui peuvent être utilisées pour sérialiser des objets dans des documents ou des flux au format JSON.</span><span class="sxs-lookup"><span data-stu-id="bddb6-120">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
