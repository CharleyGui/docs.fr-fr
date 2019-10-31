---
title: Programmer avec des assemblys
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
ms.openlocfilehash: 9f07d36d9e47189d53e367fd1406e5684c024aa3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107055"
---
# <a name="program-with-assemblies"></a>Programmer avec des assemblys
Les assemblys sont les éléments de base du .NET Framework. Ils forment l’unité fondamentale de déploiement, de gestion de version, de réutilisation, de portée d’activation et des autorisations de sécurité. Un assembly fournit au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type. Il s’agit d’une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité. Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.  
  
 Cette section explique comment créer des modules, comment créer des assemblys à partir de modules, comment créer une paire de clés et signer un assembly avec un nom fort, et comment installer un assembly dans le Global Assembly Cache. Elle décrit également comment utiliser le [désassembleur MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) pour afficher les informations de manifeste d’assembly.  
  
> [!NOTE]
> À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime chargé actuellement. Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Créer des assemblys](create.md)  
 Fournit une vue d'ensemble des assemblys multifichiers et à fichier unique.  
  
 [Noms d’assemblys](names.md)  
 Fournit une vue d’ensemble de l’affectation de noms à des assemblys.  
  
 [Comment : déterminer le nom qualifié complet d’un assembly](find-fully-qualified-name.md)  
 Décrit comment déterminer le nom complet d’un assembly.  
  
 [Exécuter des applications intranet en confiance totale](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Décrit comment spécifier la stratégie de sécurité héritée pour les assemblys de confiance totale sur un partage intranet.  
  
 [Emplacement de l’assembly](location.md)  
 Offre une vue d’ensemble de l’emplacement des assemblys.  
  
 [Comment : générer un assembly à fichier unique](../../framework/app-domains/build-single-file-assembly.md)  
 Décrit comment créer un assembly à fichier unique.  
  
 [Assemblys multifichiers](../../framework/app-domains/multifile-assemblies.md)  
 Décrit les raisons justifiant la création d’assemblys multifichiers.  
  
 [Comment : générer un assembly multifichier](../../framework/app-domains/build-multifile-assembly.md)  
 Décrit comment créer un assembly multifichier.  
  
 [Définir des attributs d’assembly](set-attributes.md)  
 Décrit les attributs d’assembly et comment les définir.  
  
 [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)  
 Explique comment et pourquoi signer un assembly avec un nom fort. Inclut des procédures.  
  
 [Temporiser la signature d’un assembly](delay-sign.md)  
 Décrit comment différer la signature d’un assembly.  
  
 [Utiliser des assemblys et le Global Assembly Cache](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Explique comment et pourquoi ajouter des assemblys au Global Assembly Cache. Inclut des procédures.  
  
 [Comment : afficher le contenu d’un assembly](view-contents.md)  
 Décrit comment utiliser le désassembleur MSIL (Ildasm.exe) pour afficher le contenu d’un assembly.  
  
 [Transfert de type dans le common language runtime](type-forwarding.md)  
 Décrit comment utiliser le transfert de type pour déplacer un type dans un assembly différent sans interrompre les applications existantes.  
  
## <a name="reference"></a>Reference  
 <xref:System.Reflection.Assembly>  
 Classe .NET Framework qui représente un assembly.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Comment : obtenir des informations sur les types et les membres à partir d’un assembly](../../framework/reflection-and-codedom/get-type-member-information.md)  
 Décrit comment obtenir par programmation des informations relatives au type et à d’autres éléments à partir d’un assembly.  
  
 [Assemblys dans .NET](index.md)  
 Offre une vue d’ensemble conceptuelle des assemblys du common language runtime.  
  
 [Contrôle de version des assemblys](versioning.md)  
 Offre une vue d’ensemble de la liaison d’assembly et des attributs <xref:System.Reflection.AssemblyVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute>.  
  
 [Méthode de localisation des assemblys par le runtime](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 Décrit comment le runtime détermine l’assembly à utiliser pour répondre à une demande de liaison.  
  
 [Réflexion](../../framework/reflection-and-codedom/reflection.md)   
 Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.
