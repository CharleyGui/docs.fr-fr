---
title: Garantie de l'intégrité des données à l'aide des codes de hachage
description: Apprenez à garantir l’intégrité des données à l’aide de codes de hachage dans .NET. Une valeur de hachage est une valeur numérique de longueur fixe qui identifie les données de manière unique.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET], hash
- data integrity
- checking hash codes
- encryption [.NET], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 3205e37f283cb205f5edfc5948a9cb9f7256f752
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556954"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="bed5b-104">Garantie de l'intégrité des données à l'aide des codes de hachage</span><span class="sxs-lookup"><span data-stu-id="bed5b-104">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="bed5b-105">Une valeur de hachage est une valeur numérique de longueur fixe qui identifie les données de manière unique.</span><span class="sxs-lookup"><span data-stu-id="bed5b-105">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="bed5b-106">Les valeurs de hachage permettent de représenter les grandes quantités de données sous forme de valeurs numériques beaucoup plus petites pour qu'elles puissent être utilisées avec des signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="bed5b-106">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="bed5b-107">Il est plus efficace de signer une valeur de hachage que de signer une valeur élevée.</span><span class="sxs-lookup"><span data-stu-id="bed5b-107">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="bed5b-108">De même, les valeurs de hachage s'avèrent utiles pour vérifier l'intégrité des données envoyées via des canaux non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="bed5b-108">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="bed5b-109">La valeur de hachage des données reçues peut être comparée à celle des données envoyées pour déterminer si les données ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="bed5b-109">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
<span data-ttu-id="bed5b-110">Cette rubrique explique comment générer et vérifier des codes de hachage en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="bed5b-110">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="bed5b-111">Génération d'un hachage</span><span class="sxs-lookup"><span data-stu-id="bed5b-111">Generating a Hash</span></span>

 <span data-ttu-id="bed5b-112">Les classes de hachage managées peuvent hacher un tableau d'octets ou un objet de flux managé.</span><span class="sxs-lookup"><span data-stu-id="bed5b-112">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="bed5b-113">Dans l'exemple suivant, l'algorithme de hachage SHA1 est utilisé pour créer une valeur de hachage pour une chaîne.</span><span class="sxs-lookup"><span data-stu-id="bed5b-113">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="bed5b-114">L'exemple utilise la classe <xref:System.Text.UnicodeEncoding> pour convertir la chaîne en tableau d'octets qui sont hachés à l'aide de la classe <xref:System.Security.Cryptography.SHA256>.</span><span class="sxs-lookup"><span data-stu-id="bed5b-114">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA256> class.</span></span> <span data-ttu-id="bed5b-115">La valeur de hachage est ensuite affichée dans la console.</span><span class="sxs-lookup"><span data-stu-id="bed5b-115">The hash value is then displayed to the console.</span></span>  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="bed5b-116">Ce code affiche la chaîne suivante dans la console :</span><span class="sxs-lookup"><span data-stu-id="bed5b-116">This code will display the following string to the console:</span></span>  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="bed5b-117">Vérification d'un hachage</span><span class="sxs-lookup"><span data-stu-id="bed5b-117">Verifying a Hash</span></span>

 <span data-ttu-id="bed5b-118">Les données peuvent être comparées à une valeur de hachage pour déterminer leur intégrité.</span><span class="sxs-lookup"><span data-stu-id="bed5b-118">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="bed5b-119">En règle générale, les données sont hachées à un certain moment et la valeur de hachage est protégée d'une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="bed5b-119">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="bed5b-120">Par la suite, les données peuvent être hachées à nouveau et comparées à la valeur protégée.</span><span class="sxs-lookup"><span data-stu-id="bed5b-120">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="bed5b-121">Si les valeurs de hachage correspondent, cela signifie que les données n'ont pas été modifiées.</span><span class="sxs-lookup"><span data-stu-id="bed5b-121">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="bed5b-122">Si les valeurs ne correspondent pas, les données ont été endommagées.</span><span class="sxs-lookup"><span data-stu-id="bed5b-122">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="bed5b-123">Pour que ce système fonctionne, le hachage protégé doit être chiffré ou tenu secret de toutes les tiers non approuvés.</span><span class="sxs-lookup"><span data-stu-id="bed5b-123">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="bed5b-124">Dans l'exemple suivant, la valeur de hachage précédente d'une chaîne est comparée à une nouvelle valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="bed5b-124">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="bed5b-125">Dans cet exemple, chaque octet des valeurs de hachage est parcouru en boucle et une comparaison est effectuée.</span><span class="sxs-lookup"><span data-stu-id="bed5b-125">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="bed5b-126">Si les deux valeurs de hachage correspondent, voici ce que ce code affiche dans la console :</span><span class="sxs-lookup"><span data-stu-id="bed5b-126">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="bed5b-127">Si elles ne correspondent pas, le code affiche ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bed5b-127">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="bed5b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bed5b-128">See also</span></span>

- [<span data-ttu-id="bed5b-129">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bed5b-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="bed5b-130">services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="bed5b-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="bed5b-131">Chiffrement multiplateforme</span><span class="sxs-lookup"><span data-stu-id="bed5b-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="bed5b-132">Protection des données ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bed5b-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
