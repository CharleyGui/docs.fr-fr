---
title: Composer des flux
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
ms.openlocfilehash: 93295c1d70f510ef563abc3a191d6690b1174fa8
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188573"
---
# <a name="compose-streams"></a><span data-ttu-id="11575-102">Composer des flux</span><span class="sxs-lookup"><span data-stu-id="11575-102">Compose streams</span></span>
<span data-ttu-id="11575-103">Un *magasin* de stockage est un support de stockage, tel qu’un disque ou une mémoire.</span><span class="sxs-lookup"><span data-stu-id="11575-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="11575-104">Chaque magasin de stockage implémente son propre flux en tant qu’implémentation de la classe <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="11575-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="11575-105">Chaque type de flux lit et écrit des octets depuis et vers le magasin de stockage donné.</span><span class="sxs-lookup"><span data-stu-id="11575-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="11575-106">Les flux qui se connectent aux magasins de stockage sont appelés des *flux de base* .</span><span class="sxs-lookup"><span data-stu-id="11575-106">Streams that connect to backing stores are called *base streams* .</span></span> <span data-ttu-id="11575-107">Les flux de base comprennent des constructeurs qui ont les paramètres nécessaires pour connecter le flux au magasin de stockage.</span><span class="sxs-lookup"><span data-stu-id="11575-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="11575-108">Par exemple, <xref:System.IO.FileStream> comprend des constructeurs qui spécifient un paramètre de chemin, qui indique la façon dont le fichier est partagé par les processus.</span><span class="sxs-lookup"><span data-stu-id="11575-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="11575-109">La conception des classes <xref:System.IO> fournit une composition simplifiée des flux.</span><span class="sxs-lookup"><span data-stu-id="11575-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="11575-110">Vous pouvez attacher des flux de base à un ou plusieurs flux directs qui fournissent les fonctionnalités souhaitées.</span><span class="sxs-lookup"><span data-stu-id="11575-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="11575-111">Vous pouvez attacher un lecteur ou un enregistreur à la fin de la chaîne pour que les types préférés puissent être lus ou écrits facilement.</span><span class="sxs-lookup"><span data-stu-id="11575-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="11575-112">L’exemple de code suivant crée un **FileStream** autour du fichier *MyFile.txt* existant afin de placer *MyFile.txt* dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="11575-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt* .</span></span> <span data-ttu-id="11575-113">Notez que les **FileStreams** sont mis en mémoire tampon par défaut.</span><span class="sxs-lookup"><span data-stu-id="11575-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="11575-114">L’exemple suppose qu’un fichier nommé *MyFile.txt* existe déjà dans le dossier où se trouve l’application.</span><span class="sxs-lookup"><span data-stu-id="11575-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="11575-115">Exemple : utilisation de StreamReader</span><span class="sxs-lookup"><span data-stu-id="11575-115">Example: Use StreamReader</span></span>
<span data-ttu-id="11575-116">L’exemple suivant crée un <xref:System.IO.StreamReader> pour lire les caractères à partir du **FileStream** , qui est passé à **StreamReader** en tant qu’argument de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="11575-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream** , which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="11575-117">Ensuite, <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> lit jusqu’à ce que <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> ne détecte plus aucun caractère.</span><span class="sxs-lookup"><span data-stu-id="11575-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="11575-118">Exemple : utilisation de BinaryReader</span><span class="sxs-lookup"><span data-stu-id="11575-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="11575-119">L’exemple suivant crée un <xref:System.IO.BinaryReader> pour lire les octets à partir du **FileStream** , qui est passé à **BinaryReader** en tant qu’argument de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="11575-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream** , which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="11575-120">Ensuite, <xref:System.IO.BinaryReader.ReadByte%2A> lit jusqu’à ce que <xref:System.IO.BinaryReader.PeekChar%2A> ne détecte plus aucun octet.</span><span class="sxs-lookup"><span data-stu-id="11575-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="11575-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11575-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
