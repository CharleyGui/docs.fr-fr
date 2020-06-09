---
title: 'Comment : utiliser la protection des données'
description: Découvrez comment utiliser la protection des données en accédant à l’API de protection des données (DPAPI) dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598591"
---
# <a name="how-to-use-data-protection"></a>Comment : utiliser la protection des données
.NET Framework fournit l'accès à l'API de protection des données (DPAPI), qui permet de chiffrer des données à l'aide des informations de compte de l'utilisateur ou de l'ordinateur actuel.  Quand vous utilisez l'API de protection des données, vous simplifiez le processus de génération et de stockage explicites de la clé de chiffrement.  
  
 Utilisez la classe <xref:System.Security.Cryptography.ProtectedMemory> pour chiffrer un tableau d'octets en mémoire.  Cette fonctionnalité est disponible dans Microsoft Windows XP et les systèmes d’exploitation ultérieurs.  Vous pouvez spécifier que la mémoire chiffrée par le processus actuel peut être déchiffrée par le processus actuel uniquement, par tous les processus ou dans le même contexte utilisateur.  Reportez-vous à l'énumération <xref:System.Security.Cryptography.MemoryProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedMemory>.  
  
 Utilisez la classe <xref:System.Security.Cryptography.ProtectedData> pour chiffrer une copie d'un tableau d'octets. Cette fonctionnalité est disponible dans Microsoft Windows 2000 et les systèmes d'exploitation ultérieurs.  Vous pouvez spécifier que les données chiffrées par le compte d'utilisateur actuel peuvent être déchiffrées uniquement par le même compte d'utilisateur, ou bien par n'importe quel compte de l'ordinateur.  Reportez-vous à l'énumération <xref:System.Security.Cryptography.DataProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedData>.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Pour chiffrer les données en mémoire à l'aide de la protection des données  
  
1. Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection de mémoire.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Pour déchiffrer les données en mémoire à l'aide de la protection des données  
  
1. Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection de mémoire.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Pour chiffrer les données d'un fichier ou d'un flux à l'aide de la protection des données  
  
1. Créez une entropie aléatoire.  
  
2. Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection des données.  
  
3. Écrivez les données chiffrées dans un fichier ou un flux.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Pour déchiffrer les données à partir d'un fichier ou d'un flux à l'aide de la protection des données  
  
1. Lisez les données chiffrées à partir d'un fichier ou d'un flux.  
  
2. Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection des données.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre deux formes de chiffrement et de déchiffrement.  Tout d'abord, l'exemple de code chiffre et déchiffre un tableau d'octets en mémoire.  Ensuite, l'exemple de code chiffre une copie d'un tableau d'octets, l'enregistre dans un fichier, charge les données à partir du fichier, puis déchiffre les données.  L'exemple affiche les données d'origine, les données chiffrées et les données déchiffrées.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Incluez une référence à `System.Security.dll`.  
  
- Incluez les espaces de noms <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> et <xref:System.Text>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
