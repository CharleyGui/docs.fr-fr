---
title: Garantie de l'intégrité des données à l'aide des codes de hachage
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 98bdce59ccbbb3b1d00ea5521169214c2bd7a10b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706199"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="89761-102">Garantie de l'intégrité des données à l'aide des codes de hachage</span><span class="sxs-lookup"><span data-stu-id="89761-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="89761-103">Une valeur de hachage est une valeur numérique de longueur fixe qui identifie les données de manière unique.</span><span class="sxs-lookup"><span data-stu-id="89761-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="89761-104">Les valeurs de hachage permettent de représenter les grandes quantités de données sous forme de valeurs numériques beaucoup plus petites pour qu'elles puissent être utilisées avec des signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="89761-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="89761-105">Il est plus efficace de signer une valeur de hachage que de signer une valeur élevée.</span><span class="sxs-lookup"><span data-stu-id="89761-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="89761-106">De même, les valeurs de hachage s'avèrent utiles pour vérifier l'intégrité des données envoyées via des canaux non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="89761-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="89761-107">La valeur de hachage des données reçues peut être comparée à celle des données envoyées pour déterminer si les données ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="89761-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="89761-108">Cette rubrique explique comment générer et vérifier des codes de hachage en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89761-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="89761-109">Génération d'un hachage</span><span class="sxs-lookup"><span data-stu-id="89761-109">Generating a Hash</span></span>  
 <span data-ttu-id="89761-110">Les classes de hachage managées peuvent hacher un tableau d'octets ou un objet de flux managé.</span><span class="sxs-lookup"><span data-stu-id="89761-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="89761-111">Dans l'exemple suivant, l'algorithme de hachage SHA1 est utilisé pour créer une valeur de hachage pour une chaîne.</span><span class="sxs-lookup"><span data-stu-id="89761-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="89761-112">L'exemple utilise la classe <xref:System.Text.UnicodeEncoding> pour convertir la chaîne en tableau d'octets qui sont hachés à l'aide de la classe <xref:System.Security.Cryptography.SHA1Managed>.</span><span class="sxs-lookup"><span data-stu-id="89761-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="89761-113">La valeur de hachage est ensuite affichée dans la console.</span><span class="sxs-lookup"><span data-stu-id="89761-113">The hash value is then displayed to the console.</span></span>  

 <span data-ttu-id="89761-114">En raison de problèmes de collision avec SHA1, Microsoft recommande SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="89761-114">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="89761-115">Ce code affiche la chaîne suivante dans la console :</span><span class="sxs-lookup"><span data-stu-id="89761-115">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="89761-116">Vérification d'un hachage</span><span class="sxs-lookup"><span data-stu-id="89761-116">Verifying a Hash</span></span>  
 <span data-ttu-id="89761-117">Les données peuvent être comparées à une valeur de hachage pour déterminer leur intégrité.</span><span class="sxs-lookup"><span data-stu-id="89761-117">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="89761-118">En règle générale, les données sont hachées à un certain moment et la valeur de hachage est protégée d'une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="89761-118">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="89761-119">Par la suite, les données peuvent être hachées à nouveau et comparées à la valeur protégée.</span><span class="sxs-lookup"><span data-stu-id="89761-119">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="89761-120">Si les valeurs de hachage correspondent, cela signifie que les données n'ont pas été modifiées.</span><span class="sxs-lookup"><span data-stu-id="89761-120">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="89761-121">Si les valeurs ne correspondent pas, les données ont été endommagées.</span><span class="sxs-lookup"><span data-stu-id="89761-121">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="89761-122">Pour que ce système fonctionne, le hachage protégé doit être chiffré ou tenu secret de toutes les tiers non approuvés.</span><span class="sxs-lookup"><span data-stu-id="89761-122">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="89761-123">Dans l'exemple suivant, la valeur de hachage précédente d'une chaîne est comparée à une nouvelle valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="89761-123">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="89761-124">Dans cet exemple, chaque octet des valeurs de hachage est parcouru en boucle et une comparaison est effectuée.</span><span class="sxs-lookup"><span data-stu-id="89761-124">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="89761-125">Si les deux valeurs de hachage correspondent, voici ce que ce code affiche dans la console :</span><span class="sxs-lookup"><span data-stu-id="89761-125">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="89761-126">Si elles ne correspondent pas, le code affiche ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="89761-126">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="89761-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89761-127">See also</span></span>

- [<span data-ttu-id="89761-128">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="89761-128">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
