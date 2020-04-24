---
title: Sérialisation XML et SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: dcb2ed1703473be582a12f430d2e051d8a420230
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588375"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="c1a61-102">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="c1a61-102">XML and SOAP serialization</span></span>

<span data-ttu-id="c1a61-103">La sérialisation XML convertit (sérialise) les champs et les propriétés publics d’un objet, ainsi que les paramètres et les valeurs de retour des méthodes, en un flux XML conforme à un document en langage XSD (XML Schema Definition) spécifique.</span><span class="sxs-lookup"><span data-stu-id="c1a61-103">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="c1a61-104">La sérialisation XML permet d'obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format série (dans ce cas, XML) pour le stockage ou le transport.</span><span class="sxs-lookup"><span data-stu-id="c1a61-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="c1a61-105">XML étant une norme ouverte, le flux de données XML peut être traité si nécessaire par toute application, quelle que soit la plateforme.</span><span class="sxs-lookup"><span data-stu-id="c1a61-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="c1a61-106">Par exemple, les services Web XML créés à l'aide d'ASP.NET utilisent la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML qui passent des données entre des applications de services Web XML sur Internet ou des intranets.</span><span class="sxs-lookup"><span data-stu-id="c1a61-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="c1a61-107">Inversement, la désérialisation utilise le flux de données XML et reconstruit l'objet.</span><span class="sxs-lookup"><span data-stu-id="c1a61-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="c1a61-108">La sérialisation XML peut également être utilisée pour sérialiser des objets en flux XML se conformant à la spécification SOAP.</span><span class="sxs-lookup"><span data-stu-id="c1a61-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="c1a61-109">SOAP est un protocole basé sur XML, conçu spécifiquement pour transporter des appels de procédure à l'aide de XML.</span><span class="sxs-lookup"><span data-stu-id="c1a61-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="c1a61-110">Pour sérialiser ou désérialiser des objets, utilisez la classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c1a61-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="c1a61-111">Pour créer les classes à sérialiser, utilisez l'outil XML Schema Definition.</span><span class="sxs-lookup"><span data-stu-id="c1a61-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1a61-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1a61-112">See also</span></span>

- [<span data-ttu-id="c1a61-113">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="c1a61-113">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="c1a61-114">[Services Web XML créés à l’aide des clients de service Web XML et ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c1a61-114">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
