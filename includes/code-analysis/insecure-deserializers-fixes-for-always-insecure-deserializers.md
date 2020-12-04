---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586695"
---
- <span data-ttu-id="09fe7-101">Si possible, utilisez plutôt un sérialiseur sécurisé et **n’autorisez pas une personne malveillante à spécifier un type arbitraire à désérialiser**.</span><span class="sxs-lookup"><span data-stu-id="09fe7-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="09fe7-102">Certains sérialiseurs plus sûrs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="09fe7-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="09fe7-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Ne jamais utiliser <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="09fe7-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="09fe7-104">Si vous devez utiliser un programme de résolution de type, limitez les types désérialisés à une liste attendue.</span><span class="sxs-lookup"><span data-stu-id="09fe7-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="09fe7-105">Newtonsoft Json.NET-utilise TypeNameHandling. None.</span><span class="sxs-lookup"><span data-stu-id="09fe7-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="09fe7-106">Si vous devez utiliser une autre valeur pour TypeNameHandling, limitez les types désérialisés à une liste attendue avec un ISerializationBinder personnalisé.</span><span class="sxs-lookup"><span data-stu-id="09fe7-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="09fe7-107">Mémoires tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="09fe7-107">Protocol Buffers</span></span>

- <span data-ttu-id="09fe7-108">Rendez la falsification des données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="09fe7-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="09fe7-109">Après la sérialisation, signez les données sérialisées par chiffrement.</span><span class="sxs-lookup"><span data-stu-id="09fe7-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="09fe7-110">Avant la désérialisation, validez la signature de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="09fe7-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="09fe7-111">Empêcher la clé de chiffrement d’être divulguée et concevoir des rotations de clés.</span><span class="sxs-lookup"><span data-stu-id="09fe7-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
