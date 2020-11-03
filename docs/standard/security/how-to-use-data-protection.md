---
title: 'Procédure : utiliser la protection des données'
description: Découvrez comment utiliser la protection des données en accédant à l’API de protection des données (DPAPI) dans .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: d3fe7ef3ddbc6e75a248101829b11a8abcb3c15a
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282051"
---
# <a name="how-to-use-data-protection"></a>Procédure : utiliser la protection des données

> [!NOTE]
> Cet article s’applique à Windows.
>
> Pour plus d’informations sur la ASP.NET Core, consultez [protection des données ASP.net Core](/aspnet/core/security/data-protection/introduction).

.NET fournit un accès à l’API de protection des données (DPAPI), qui vous permet de chiffrer les données à l’aide des informations du compte d’utilisateur ou de l’ordinateur actuel.  Quand vous utilisez l'API de protection des données, vous simplifiez le processus de génération et de stockage explicites de la clé de chiffrement.  
  
Utilisez la classe <xref:System.Security.Cryptography.ProtectedData> pour chiffrer une copie d'un tableau d'octets. Cette fonctionnalité est disponible dans .NET Framework, .NET Core et .NET 5.  Vous pouvez spécifier que les données chiffrées par le compte d'utilisateur actuel peuvent être déchiffrées uniquement par le même compte d'utilisateur, ou bien par n'importe quel compte de l'ordinateur.  Reportez-vous à l'énumération <xref:System.Security.Cryptography.DataProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedData>.  
  
## <a name="encrypt-data-to-a-file-or-stream-using-data-protection"></a>Chiffrer des données dans un fichier ou un flux à l’aide de la protection des données  
  
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

Cet exemple compile et s’exécute uniquement lorsque vous ciblez .NET Framework et que vous exécutez sur Windows.

- Incluez une référence à `System.Security.dll`.  
  
- Incluez les espaces de noms <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> et <xref:System.Text>.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de chiffrement](cryptography-model.md)
- [services de chiffrement](cryptographic-services.md)
- [Chiffrement multiplateforme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
