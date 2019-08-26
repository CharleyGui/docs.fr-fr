---
title: Programmation à l'aide d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921434"
---
# <a name="programming-with-assemblies"></a>Programmation à l'aide d'assemblys
Les assemblys sont les éléments de base du .NET Framework. Ils forment l’unité fondamentale de déploiement, de gestion de version, de réutilisation, de portée d’activation et des autorisations de sécurité. Un assembly fournit au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type. Il s’agit d’une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité. Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.  
  
 Cette section explique comment créer des modules, comment créer des assemblys à partir de modules, comment créer une paire de clés et signer un assembly avec un nom fort, et comment installer un assembly dans le Global Assembly Cache. Elle décrit également comment utiliser le [désassembleur MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour afficher les informations de manifeste d’assembly.  
  
> [!NOTE]
> À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime actuellement chargé. Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)  
 Fournit une vue d'ensemble des assemblys multifichiers et à fichier unique.  
  
 [Noms d’assemblys](../../../docs/framework/app-domains/assembly-names.md)  
 Fournit une vue d’ensemble de l’affectation de noms à des assemblys.  
  
 [Guide pratique pour déterminer le nom qualifié complet d’un assembly](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Décrit comment déterminer le nom complet d’un assembly.  
  
 [Exécution d'applications intranet de confiance totale](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Décrit comment spécifier la stratégie de sécurité héritée pour les assemblys de confiance totale sur un partage intranet.  
  
 [Emplacement de l'assembly](../../../docs/framework/app-domains/assembly-location.md)  
 Offre une vue d’ensemble de l’emplacement des assemblys.  
  
 [Guide pratique pour générer un assembly à fichier unique](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Décrit comment créer un assembly à fichier unique.  
  
 [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Décrit les raisons justifiant la création d’assemblys multifichiers.  
  
 [Guide pratique pour générer un assembly multifichier](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Décrit comment créer un assembly multifichier.  
  
 [Définition des attributs d’assembly](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Décrit les attributs d’assembly et comment les définir.  
  
 [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Explique comment et pourquoi signer un assembly avec un nom fort. Inclut des procédures.  
  
 [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Décrit comment différer la signature d’un assembly.  
  
 [Utilisation d’assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Explique comment et pourquoi ajouter des assemblys au Global Assembly Cache. Inclut des procédures.  
  
 [Guide pratique pour afficher le contenu d’un assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Décrit comment utiliser le désassembleur MSIL (Ildasm.exe) pour afficher le contenu d’un assembly.  
  
 [Transfert de type dans le Common Language Runtime](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Décrit comment utiliser le transfert de type pour déplacer un type dans un assembly différent sans interrompre les applications existantes.  
  
## <a name="reference"></a>Référence  
 <xref:System.Reflection.Assembly>  
 Classe .NET Framework qui représente un assembly.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour obtenir des informations relatives au type et aux membres à partir d’un assembly](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Décrit comment obtenir par programmation des informations relatives au type et à d’autres éléments à partir d’un assembly.  
  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Offre une vue d’ensemble conceptuelle des assemblys du common language runtime.  
  
 [Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md)  
 Offre une vue d’ensemble de la liaison d’assembly et des attributs <xref:System.Reflection.AssemblyVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute>.  
  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Décrit comment le runtime détermine l’assembly à utiliser pour répondre à une demande de liaison.  
  
 [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.
