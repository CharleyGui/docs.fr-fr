---
title: Versioning des assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d295f394a9ce7f038e2c64d42193e2d18040a98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921664"
---
# <a name="assembly-versioning"></a>Versioning des assemblys
Tout le versioning des assemblys qui utilisent le Common Language Runtime est effectué au niveau de l'assembly. La version spécifique d'un assembly et les versions des assemblys dépendants sont enregistrées dans le manifeste d'assembly. La stratégie de version par défaut du runtime est la suivante : les applications s'exécutent uniquement avec les versions dans lesquelles elles ont été générées et testées, sauf en cas de substitution par une stratégie de version explicite dans des fichiers de configuration (le fichier de configuration de l'application, le fichier de stratégie de l'éditeur et le fichier de configuration de l'administrateur de l'ordinateur).  
  
> [!NOTE]
> Le versioning est uniquement effectué sur les assemblys avec des noms forts.  
  
 Le runtime procède en plusieurs étapes pour résoudre une demande de liaison d'assembly :  
  
1. Il vérifie la référence de l'assembly d'origine afin de déterminer la version de l'assembly à lier.  
  
2. Il recherche tous les fichiers de configuration applicables pour appliquer la stratégie de version.  
  
3. Il détermine l'assembly correct à partir de la référence de l'assembly d'origine et de toute redirection spécifiée dans les fichiers de configuration et il définit la version qui doit être liée à l'assembly d'appel.  
  
4. Il vérifie le Global Assembly Cache, les codes base spécifiés dans les fichiers de configuration, puis le répertoire et les sous-répertoires de l’application en utilisant les règles de recherche expliquées dans [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 L’illustration suivante indique ces étapes :  
  
 ![Diagramme qui montre les étapes de la résolution des demandes de liaison d’assemblys.](./media/assembly-versioning/resolve-assembly-binding-request.gif)
  
 Pour plus d’informations sur la configuration des applications, consultez [Configuration d’applications](../../../docs/framework/configure-apps/index.md). Pour plus d’informations sur la stratégie de liaison, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Informations sur la version  
 Chaque assembly possède deux modes distincts d'expression d'informations sur la version :  
  
- Le numéro de version de l'assembly qui, avec le nom de l'assembly et les informations sur la culture, fait partie de l'identité de l'assembly. Ce numéro est utilisé par le runtime pour appliquer la stratégie de version et joue un rôle essentiel dans le processus de résolution des types au moment de l'exécution.  
  
- Une version d'informations, qui correspond à une chaîne représentant des informations supplémentaires sur la version incluses à des fins d'information uniquement.  
  
### <a name="assembly-version-number"></a>Numéro de version de l'assembly  
 Chaque assembly possède un numéro de version faisant partie de son identité. Deux assemblys dont les numéros de versions diffèrent sont de ce fait considérés par le runtime comme étant des assemblys complètement différents. Ce numéro de version est physiquement représenté par une chaîne en quatre parties au format suivant :  
  
 \<*version majeure*>.\< *version mineure*>.\< *numéro de build*>.\< *révision*>  
  
 Par exemple, la version 1.5.1254.0 indique que 1 est la version principale, 5 la version secondaire, 1254 le numéro de build et 0 le numéro de révision.  
  
 Le numéro de version est stocké dans le manifeste d'assembly avec d'autres informations sur l'identité, parmi lesquelles le nom de l'assembly et la clé publique, ainsi que des informations sur les relations et les identités des autres assemblys connectés à l'application.  
  
 Lors de la génération d'un assembly, l'outil de développement enregistre des informations sur la dépendance de chaque assembly qui est référencé dans le manifeste d'assembly. Le runtime utilise ces numéros de version, ainsi que des informations sur la configuration définies par un administrateur, une application ou un éditeur, pour charger la version correcte d'un assembly référencé.  
  
 Le runtime fait la différence entre les assemblys normaux et les assemblys avec nom fort à des fins de versioning. La vérification de la version n'est effectuée qu'avec les assemblys avec nom fort.  
  
 Pour plus d’informations sur la spécification des stratégies de liaison de version, consultez [Configuration d’applications](../../../docs/framework/configure-apps/index.md). Pour plus d’informations sur l’utilisation des informations sur la version par le runtime pour rechercher un assembly particulier, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Version d'informations sur l'assembly  
 La version d'informations correspond à une chaîne qui attache des informations supplémentaires sur la version à un assembly à des fins d'information uniquement ; ces informations ne sont pas utilisées au moment de l'exécution. La version d'informations en mode texte correspond à la documentation marketing, au coffret et au nom de produit du produit et n'est pas utilisée par le runtime. Par exemple, une version d'informations pourrait être "Version 1.0 du Common Language Runtime » ou « Contrôle NET SP 2". Sous Microsoft Windows, ces informations apparaissent dans l'élément "Product Version" de l'onglet Version de la boîte de dialogue des propriétés du fichier.  
  
> [!NOTE]
> Même si tout type de texte peut être spécifié, un message d'avertissement apparaît à la compilation si le format de la chaîne n'est pas celui qui est utilisé par le numéro de version de l'assembly ou si le format est correct mais contient des caractères génériques. Cet avertissement est sans incidence.  
  
 La version d'informations est représentée à l'aide de l'attribut personnalisé <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>. Pour plus d’informations sur les informations de l’attribut de version, consultez [Définition des attributs d’assembly](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Configuration d'applications](../../../docs/framework/configure-apps/index.md)
- [Définition des attributs d’assembly](../../../docs/framework/app-domains/set-assembly-attributes.md)
- [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
