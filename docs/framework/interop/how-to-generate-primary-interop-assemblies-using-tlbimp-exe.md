---
title: 'Procédure : générer des assemblys PIA à l’aide de Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b093f9bb633578cc0051cfca7b1362f8bf097d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662447"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Procédure : générer des assemblys PIA à l’aide de Tlbimp.exe

Il existe deux manières de générer un assembly PIA :

- À l’aide de [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), fourni dans le Kit de développement de logiciel (SDK) Windows.

  La façon la plus simple de générer un assembly PIA est d’utiliser l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe offre les protections suivantes :

  - Il vérifie les autres assemblys PIA inscrits avant de créer de nouveaux assemblys PIA pour les références de bibliothèque de types imbriquées.

  - Il n'émet pas d'assembly PIA si vous ne spécifiez pas le conteneur ou le nom de fichier pour attribuer un nom fort à l'assembly PIA.

  - Il n'émet pas d'assembly PIA si vous omettez les références aux assemblys dépendants.

  - Il n'émet pas d'assembly PIA si vous ajoutez des références à des assemblys dépendants qui ne sont pas des assemblys PIA.

- Par la création manuelle d'assemblys PIA dans le code source avec un langage conforme à la spécification CLS, tel que le C#. Cette approche est utile quand aucune bibliothèque de types n'est disponible.

Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement. Pour plus d’informations, consultez [Création d’une paire de clés](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Pour générer des assemblys PIA à l'aide de Tlbimp.exe

1. À l'invite de commandes, tapez :

    **tlbimp** *fichiertlb*  **/primary /keyfile:** *nomfichier* **/out:** *nomassembly*

    Dans cette commande, *fichiertlb* correspond au fichier contenant la bibliothèque de types COM, *nomfichier* au nom du conteneur ou du fichier qui contient la paire de clés, et *nomassembly* au nom de l’assembly à signer avec un nom fort.

Les assemblys PIA peuvent référencer uniquement d'autres assemblys PIA. Si votre assembly référence des types d'une bibliothèque de types COM tiers, vous devrez obtenir un assembly PIA auprès de l'éditeur avant de pouvoir générer votre assembly PIA. Si vous êtes l'éditeur, vous devrez générer un assembly PIA pour la bibliothèque de types dépendante avant de générer l'assembly PIA de référence.

Un assembly PIA avec un numéro de version différent de celui de la bibliothèque de types d'origine ne pourra pas être détecté s'il est installé dans le répertoire actif. Vous devez inscrire l’assembly PIA dépendant dans le Registre Windows ou utiliser l’option **/reference** pour garantir que Tlbimp.exe trouve la DLL dépendante.

Vous pouvez également encapsuler plusieurs versions d'une bibliothèque de types. Pour obtenir des instructions, consultez [Guide pratique pour encapsuler plusieurs versions de bibliothèques de types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).

## <a name="example"></a>Exemples

Dans l'exemple suivant, la bibliothèque de types COM `LibUtil.tlb` est importée et l'assembly `LibUtil.dll` est signé avec un nom fort à l'aide du fichier de clé `CompanyA.snk`. En ne spécifiant pas de nom d'espace de noms, cet exemple génère l'espace de noms par défaut `LibUtil`.

```
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

Pour un nom plus descriptif (qui utilise la règle de nommage *Nom_fournisseur*.*Nom_bibliothèque*), l’exemple suivant remplace le nom de fichier d’assembly et le nom d’espace de noms par défaut.

```
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

L'exemple suivant importe `MyLib.tlb`, qui référence `CompanyA.LibUtil.dll`, et signe l'assembly `CompanyB.MyLib.dll` avec un nom fort à l'aide du fichier de clé `CompanyB.snk`. L'espace de noms `CompanyB.MyLib` remplace le nom d'espace de noms par défaut.

```
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour enregistrer des assemblys PIA](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
