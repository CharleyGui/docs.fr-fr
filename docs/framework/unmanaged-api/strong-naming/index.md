---
title: Nom fort (Informations de référence sur les API non managées)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140635"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Nom fort (Informations de référence sur les API non managées)
L’API de nommage fort permet à un client d’administrer la signature avec noms forts pour les assemblys.  
  
 La signature d'un assembly avec un nom fort ajoute un chiffrement à clé publique au fichier contenant le manifeste d'assembly. La signature avec un nom fort permet de vérifier l’unicité du nom, empêche l’usurpation de noms et fournit aux appelants une identité unique quand une référence est résolue. Aucun niveau de confiance n’est toutefois associé à un nom fort.  
  
## <a name="in-this-section"></a>Dans cette section  
  
> [!NOTE]
> Toutes ces fonctions sont dépréciées à compter de .NET Framework 4. Pour obtenir des suggestions d’alternatives, consultez l’interface [ICLRStrongName](../hosting/iclrstrongname-interface.md).  
  
 [GetHashFromAssemblyFile, fonction](gethashfromassemblyfile-function.md)  
 Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié. Dépréciée à compter de .NET Framework 4.  
  
 [GetHashFromAssemblyFileW, fonction](gethashfromassemblyfilew-function.md)  
 Obtient un hachage du fichier d’assembly spécifié sous forme de chaîne Unicode, à l’aide de l’algorithme de hachage spécifié. Dépréciée à compter de .NET Framework 4.  
  
 [GetHashFromBlob, fonction](gethashfromblob-function.md)  
 Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié. Dépréciée à compter de .NET Framework 4.  
  
 [GetHashFromFile, fonction](gethashfromfile-function.md)  
 Génère un hachage sur le contenu du fichier spécifié.  Dépréciée à compter de .NET Framework 4.  
  
 [GetHashFromFileW, fonction](gethashfromfilew-function.md)  
 Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode. Dépréciée à compter de .NET Framework 4.  
  
 [GetHashFromHandle, fonction](gethashfromhandle-function.md)  
 Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.  Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameCompareAssemblies, fonction](strongnamecompareassemblies-function.md)  
 Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameErrorInfo, fonction](strongnameerrorinfo-function.md)  
 Obtient le dernier code d’erreur déclenché par l’une des fonctions de nom fort.  
  
 [StrongNameFreeBuffer, fonction](strongnamefreebuffer-function.md)  
 Libère la mémoire qui a été alloué avec un appel précédent à une fonction de nom fort comme [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) ou [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).   Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameGetBlob, fonction](strongnamegetblob-function.md)  
 Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameGetBlobFromImage, fonction](strongnamegetblobfromimage-function.md)  
 Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameGetPublicKey, fonction](strongnamegetpublickey-function.md)  
 Obtient la clé publique à partir d’une paire de clés publique/privée. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameHashSize, fonction](strongnamehashsize-function.md)  
 Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.  Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameKeyDelete, fonction](strongnamekeydelete-function.md)  
 Supprime le conteneur de clé spécifié. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameKeyGen, fonction](strongnamekeygen-function.md)  
 Crée une nouvelle paire de clés publique/privée pour une utilisation de nom fort.  Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameKeyGenEx, fonction](strongnamekeygenex-function.md)  
 Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée pour une utilisation de nom fort. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameKeyInstall, fonction](strongnamekeyinstall-function.md)  
 Importe une paire de clés publique/privée dans un conteneur.  Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameSignatureGeneration, fonction](strongnamesignaturegeneration-function.md)  
 Génère une signature de nom fort pour l’assembly spécifié.   Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameSignatureGenerationEx, fonction](strongnamesignaturegenerationex-function.md)  
 Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.    Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameSignatureSize, fonction](strongnamesignaturesize-function.md)  
 Retourne la taille de la signature de nom fort. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameSignatureVerification, fonction](strongnamesignatureverification-function.md)  
 Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameSignatureVerificationEx, fonction](strongnamesignatureverificationex-function.md)  
 Obtient une valeur indiquant si le manifeste d’assembly au chemin fourni contient une signature de nom fort.  Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameSignatureVerificationFromImage, fonction](strongnamesignatureverificationfromimage-function.md)  
 Vérifie qu’un assembly qui a déjà été mappé en mémoire est valide pour la clé publique associée. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameTokenFromAssembly, fonction](strongnametokenfromassembly-function.md)  
 Crée un jeton de nom fort à partir du fichier d’assembly spécifié.  Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameTokenFromAssemblyEx, fonction](strongnametokenfromassemblyex-function.md)  
 Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique. Dépréciée à compter de .NET Framework 4.  
  
 [StrongNameTokenFromPublicKey, fonction](strongnametokenfrompublickey-function.md)  
 Obtient un jeton représentant une clé publique. Dépréciée à compter de .NET Framework 4.  
  
 [PublicKeyBlob, structure](publickeyblob-structure.md)  
 Représente la clé publique d’une paire de clés publique/privée au format binaire.  
  
## <a name="see-also"></a>Voir aussi

- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
- [Référence API non gestion](../index.md)
