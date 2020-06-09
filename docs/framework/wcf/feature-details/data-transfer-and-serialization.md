---
title: Transfert de données et sérialisation
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593484"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="0a98b-102">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="0a98b-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="0a98b-103">Dans un système connecté, les services et les clients se reposent sur l'échange de données pour accomplir une tâche.</span><span class="sxs-lookup"><span data-stu-id="0a98b-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="0a98b-104">En tant que développeur d’un service ou d’un client, vous devez également comprendre comment Windows Communication Foundation (WCF) gère les données et la sérialisation des données afin de créer des applications efficaces et faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="0a98b-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a98b-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0a98b-105">In This Section</span></span>  
 [<span data-ttu-id="0a98b-106">Specifying Data Transfer in Service Contracts</span><span class="sxs-lookup"><span data-stu-id="0a98b-106">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="0a98b-107">Décrit les concepts de base du transfert de données dans les services.</span><span class="sxs-lookup"><span data-stu-id="0a98b-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="0a98b-108">Using Data Contracts</span><span class="sxs-lookup"><span data-stu-id="0a98b-108">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="0a98b-109">Définit les contrats de données et la méthode utilisée pour les créer et les utiliser.</span><span class="sxs-lookup"><span data-stu-id="0a98b-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="0a98b-110">Sérialiseur de contrat de données</span><span class="sxs-lookup"><span data-stu-id="0a98b-110">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="0a98b-111">Décrit comment accomplir la sérialisation des données avec la classe <xref:System.Runtime.Serialization.DataContractSerializer> ou une extension de la classe <xref:System.Runtime.Serialization.XmlObjectSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0a98b-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="0a98b-112">Utilisation de la classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="0a98b-112">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="0a98b-113">Décrit comment et pourquoi utiliser la classe <xref:System.Xml.Serialization.XmlSerializer>, une alternative à la classe <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0a98b-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="0a98b-114">Utilisation de contrats de message</span><span class="sxs-lookup"><span data-stu-id="0a98b-114">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="0a98b-115">Décrit comment les contrats de message autorisent un contrôle pointu sur les messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="0a98b-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="0a98b-116">Utilisation de la classe message</span><span class="sxs-lookup"><span data-stu-id="0a98b-116">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="0a98b-117">Décrit comment utiliser les fonctionnalités de la classe Message.</span><span class="sxs-lookup"><span data-stu-id="0a98b-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="0a98b-118">Filtrage</span><span class="sxs-lookup"><span data-stu-id="0a98b-118">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="0a98b-119">Décrit le filtrage qui permet le pré-traitement d'un message selon différents critères.</span><span class="sxs-lookup"><span data-stu-id="0a98b-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="0a98b-120">Données volumineuses et diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="0a98b-120">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="0a98b-121">Décrit comment envoyer un grand bloc de données, tel qu'un fichier binaire.</span><span class="sxs-lookup"><span data-stu-id="0a98b-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="0a98b-122">Considérations relatives à la sécurité des données</span><span class="sxs-lookup"><span data-stu-id="0a98b-122">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="0a98b-123">Décrit des éléments à connaître lors de la programmation du transfert de données et de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="0a98b-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="0a98b-124">Vue d'ensemble de l'architecture de transfert de données</span><span class="sxs-lookup"><span data-stu-id="0a98b-124">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="0a98b-125">Décrit une vue de la conception globale du transfert de données dans WCF.</span><span class="sxs-lookup"><span data-stu-id="0a98b-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0a98b-126">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="0a98b-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="0a98b-127">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0a98b-127">Related Sections</span></span>  
 [<span data-ttu-id="0a98b-128">Extension des encodeurs et des sérialiseurs</span><span class="sxs-lookup"><span data-stu-id="0a98b-128">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="0a98b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a98b-129">See also</span></span>

- [<span data-ttu-id="0a98b-130">Meilleures pratiques : contrôle de version des contrats de données</span><span class="sxs-lookup"><span data-stu-id="0a98b-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="0a98b-131">Contrôle de version de service</span><span class="sxs-lookup"><span data-stu-id="0a98b-131">Service Versioning</span></span>](../service-versioning.md)
