---
title: Chiffrement et déchiffrement de chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: e0e3fc332bf9430b1fa56dbb7630f849d3a29c2e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072403"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Procédure pas à pas : chiffrement et déchiffrement de chaînes en Visual Basic

Cette procédure pas à pas vous montre comment utiliser la <xref:System.Security.Cryptography.DESCryptoServiceProvider> classe pour chiffrer et déchiffrer des chaînes à l’aide de la version du fournisseur de services de chiffrement (CSP) de l’algorithme Triple Data Encryption Standard ( <xref:System.Security.Cryptography.TripleDES> ). La première étape consiste à créer une classe wrapper simple qui encapsule l’algorithme 3DES et stocke les données chiffrées sous la forme d’une chaîne codée en base 64. Ce wrapper est ensuite utilisé pour stocker en toute sécurité les données utilisateur privées dans un fichier texte accessible publiquement.  
  
 Vous pouvez utiliser le chiffrement pour protéger les secrets des utilisateurs (par exemple, les mots de passe) et rendre les informations d’identification illisibles pour les utilisateurs non autorisés. Cela peut empêcher le vol de l’identité d’un utilisateur autorisé, ce qui protège les ressources de l’utilisateur et fournit une non-répudiation. Le chiffrement peut également empêcher les utilisateurs non autorisés d’accéder aux données d’un utilisateur.  
  
 Pour plus d’informations, consultez [Services de cryptographie](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
> Les algorithmes Rijndael (désormais appelé Advanced Encryption Standard [AES]) et 3DES (Triple Data Encryption Standard) offrent une plus grande sécurité que DES, car ils nécessitent beaucoup de ressources informatiques. Pour plus d’informations, consultez <xref:System.Security.Cryptography.DES> et <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Pour créer le wrapper de chiffrement  
  
1. Créez la `Simple3Des` classe pour encapsuler les méthodes de chiffrement et de déchiffrement.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Ajoutez une importation de l’espace de noms Cryptography au début du fichier qui contient la `Simple3Des` classe.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. Dans la `Simple3Des` classe, ajoutez un champ privé pour stocker le fournisseur de services de chiffrement 3DES.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Ajoutez une méthode privée qui crée un tableau d’octets d’une longueur spécifiée à partir du hachage de la clé spécifiée.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. Ajoutez un constructeur pour initialiser le fournisseur de services de chiffrement 3DES.  
  
     Le `key` paramètre contrôle les `EncryptData` `DecryptData` méthodes et.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Ajoutez une méthode publique qui chiffre une chaîne.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Ajoutez une méthode publique qui déchiffre une chaîne.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     La classe wrapper peut maintenant être utilisée pour protéger les ressources de l’utilisateur. Dans cet exemple, il est utilisé pour stocker en toute sécurité des données utilisateur privées dans un fichier texte accessible publiquement.  
  
### <a name="to-test-the-encryption-wrapper"></a>Pour tester le wrapper de chiffrement  
  
1. Dans une classe distincte, ajoutez une méthode qui utilise la méthode du wrapper `EncryptData` pour chiffrer une chaîne et l’écrire dans le dossier Mes documents de l’utilisateur.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Ajoutez une méthode qui lit la chaîne chiffrée à partir du dossier Mes documents de l’utilisateur et déchiffre la chaîne avec la `DecryptData` méthode du wrapper.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Ajoutez le code de l’interface utilisateur pour appeler les `TestEncoding` `TestDecoding` méthodes et.  
  
4. Exécutez l'application.  
  
     Lorsque vous testez l’application, Notez qu’elle ne déchiffrera pas les données si vous fournissez un mot de passe incorrect.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [services de chiffrement](../../../../standard/security/cryptographic-services.md)
