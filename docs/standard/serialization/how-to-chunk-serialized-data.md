---
title: Guide pratique pour segmenter des données sérialisées
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 6a39997d8854d525146c044ed4bbf939de615d3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602423"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="581c4-102">Guide pratique pour segmenter des données sérialisées</span><span class="sxs-lookup"><span data-stu-id="581c4-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="581c4-103">Les deux problèmes qui se produisent lors de l'envoi de grands ensembles de données dans des messages de services Web sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="581c4-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="581c4-104">Un grand jeu de travail (mémoire) en raison d'une mise en mémoire tampon effectuée par le moteur de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="581c4-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="581c4-105">Une consommation de bande passante importante due à une inflation de 33 % après un encodage Base64.</span><span class="sxs-lookup"><span data-stu-id="581c4-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="581c4-106">Pour résoudre ces problèmes, implémentez l'interface <xref:System.Xml.Serialization.IXmlSerializable> pour contrôler la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="581c4-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="581c4-107">Plus précisément, implémentez les méthodes <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> pour segmenter les données.</span><span class="sxs-lookup"><span data-stu-id="581c4-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="581c4-108">Pour implémenter la segmentation côté serveur</span><span class="sxs-lookup"><span data-stu-id="581c4-108">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="581c4-109">Sur l'ordinateur serveur, la méthode Web doit désactiver la mise en mémoire tampon ASP.NET et retourner un type qui implémente <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="581c4-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="581c4-110">Le type qui implémente <xref:System.Xml.Serialization.IXmlSerializable> segmente les données dans la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="581c4-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="581c4-111">Pour implémenter le traitement côté client</span><span class="sxs-lookup"><span data-stu-id="581c4-111">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="581c4-112">Modifiez la méthode Web sur le proxy client pour retourner le type qui implémente <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="581c4-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="581c4-113">Vous pouvez utiliser un <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> pour effectuer cette opération automatiquement (non illustrée ici).</span><span class="sxs-lookup"><span data-stu-id="581c4-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="581c4-114">Implémentez la méthode <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> pour lire le flux de données segmenté et écrire les octets sur le disque.</span><span class="sxs-lookup"><span data-stu-id="581c4-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="581c4-115">Cette implémentation déclenche également des événements de progression qui peuvent être utilisés par un contrôle graphique, tel qu'une barre de progression.</span><span class="sxs-lookup"><span data-stu-id="581c4-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="581c4-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="581c4-116">Example</span></span>  
<span data-ttu-id="581c4-117">L'exemple de code suivant illustre la méthode Web sur le client qui désactive la mise en mémoire tampon ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="581c4-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="581c4-118">Il affiche également l'implémentation côté client de l'interface <xref:System.Xml.Serialization.IXmlSerializable> qui segmente les données dans la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="581c4-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="581c4-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="581c4-119">Compiling the code</span></span>  
  
- <span data-ttu-id="581c4-120">Le code utilise les espaces de noms suivants : <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> et <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="581c4-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581c4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="581c4-121">See also</span></span>

- [<span data-ttu-id="581c4-122">Sérialisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="581c4-122">Custom Serialization</span></span>](custom-serialization.md)
