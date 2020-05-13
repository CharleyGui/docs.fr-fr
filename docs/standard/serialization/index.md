---
title: Sérialisation-.NET
description: Cet article fournit des informations sur les technologies de sérialisation .NET, y compris la sérialisation binaire, la sérialisation XML et SOAP et la sérialisation JSON.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377244"
---
# <a name="serialization-in-net"></a><span data-ttu-id="8ea9b-103">Sérialisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="8ea9b-103">Serialization in .NET</span></span>

<span data-ttu-id="8ea9b-104">La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-104">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="8ea9b-105">Le complément de la sérialisation est la désérialisation, qui convertit un flux de données en un objet.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-105">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="8ea9b-106">Ensemble, ces processus autorisent le stockage et le transfert des données.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-106">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="8ea9b-107">.NET propose les technologies de sérialisation suivantes :</span><span class="sxs-lookup"><span data-stu-id="8ea9b-107">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="8ea9b-108">[La sérialisation binaire](binary-serialization.md) préserve la fidélité du type, ce qui est utile pour conserver l’état d’un objet entre différents appels d’une application.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-108">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="8ea9b-109">Par exemple, vous pouvez partager un objet entre plusieurs applications en le sérialisant dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-109">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="8ea9b-110">Vous pouvez sérialiser un objet vers un flux, un disque, la mémoire, le réseau, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-110">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="8ea9b-111">La communication à distance utilise la sérialisation pour passer des objets « par valeur » d'un ordinateur ou d'un domaine d'application à un autre.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-111">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="8ea9b-112">[La sérialisation XML et SOAP](xml-and-soap-serialization.md) sérialise uniquement les propriétés et les champs publics et ne conserve pas la fidélité du type.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-112">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="8ea9b-113">Ceci est utile lorsque vous souhaitez fournir ou consommer des données sans restreindre l'application qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-113">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="8ea9b-114">XML étant une norme ouverte, elle constitue une option intéressante pour partager des données via le Web.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-114">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="8ea9b-115">Le protocole SOAP est également une norme ouverte et représente par conséquent une option avantageuse.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-115">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="8ea9b-116">[La sérialisation JSON](system-text-json-overview.md) sérialise uniquement les propriétés publiques et ne conserve pas la fidélité du type.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-116">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="8ea9b-117">JSON est une norme ouverte qui est un choix attrayant pour le partage de données sur le Web.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-117">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="8ea9b-118">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="8ea9b-118">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="8ea9b-119">Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-119">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="8ea9b-120">Contient des classes qui peuvent être utilisées pour sérialiser des objets en documents ou en flux de données au format XML.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-120">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="8ea9b-121">Contient des classes qui peuvent être utilisées pour sérialiser des objets dans des documents ou des flux au format JSON.</span><span class="sxs-lookup"><span data-stu-id="8ea9b-121">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
