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
# <a name="ensuring-data-integrity-with-hash-codes"></a>Garantie de l'intégrité des données à l'aide des codes de hachage
Une valeur de hachage est une valeur numérique de longueur fixe qui identifie les données de manière unique. Les valeurs de hachage permettent de représenter les grandes quantités de données sous forme de valeurs numériques beaucoup plus petites pour qu'elles puissent être utilisées avec des signatures numériques. Il est plus efficace de signer une valeur de hachage que de signer une valeur élevée. De même, les valeurs de hachage s'avèrent utiles pour vérifier l'intégrité des données envoyées via des canaux non sécurisés. La valeur de hachage des données reçues peut être comparée à celle des données envoyées pour déterminer si les données ont été modifiées.  
  
Cette rubrique explique comment générer et vérifier des codes de hachage en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography>.  
  
## <a name="generating-a-hash"></a>Génération d'un hachage

 Les classes de hachage managées peuvent hacher un tableau d'octets ou un objet de flux managé. Dans l'exemple suivant, l'algorithme de hachage SHA1 est utilisé pour créer une valeur de hachage pour une chaîne. L'exemple utilise la classe <xref:System.Text.UnicodeEncoding> pour convertir la chaîne en tableau d'octets qui sont hachés à l'aide de la classe <xref:System.Security.Cryptography.SHA256>. La valeur de hachage est ensuite affichée dans la console.  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Ce code affiche la chaîne suivante dans la console :  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a>Vérification d'un hachage

 Les données peuvent être comparées à une valeur de hachage pour déterminer leur intégrité. En règle générale, les données sont hachées à un certain moment et la valeur de hachage est protégée d'une certaine façon. Par la suite, les données peuvent être hachées à nouveau et comparées à la valeur protégée. Si les valeurs de hachage correspondent, cela signifie que les données n'ont pas été modifiées. Si les valeurs ne correspondent pas, les données ont été endommagées. Pour que ce système fonctionne, le hachage protégé doit être chiffré ou tenu secret de toutes les tiers non approuvés.  
  
 Dans l'exemple suivant, la valeur de hachage précédente d'une chaîne est comparée à une nouvelle valeur de hachage. Dans cet exemple, chaque octet des valeurs de hachage est parcouru en boucle et une comparaison est effectuée.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Si les deux valeurs de hachage correspondent, voici ce que ce code affiche dans la console :  
  
```console  
The hash codes match.  
```  
  
 Si elles ne correspondent pas, le code affiche ce qui suit :  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de chiffrement](cryptography-model.md)
- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
