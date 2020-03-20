---
title: Prise en charge de l’identifiant de ressource internationalisée dans System.Uri
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
ms.openlocfilehash: f78fff250aae177b5f0360e77a1c41a2f2bb0527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64647334"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Prise en charge de l’identifiant de ressource internationalisée dans System.Uri
La classe <xref:System.Uri?displayProperty=nameWithType> a été étendue pour prendre en charge les identificateurs IRI (International Resource Identifier) et les noms IDN (Internationalized Domain Name). Ces améliorations sont disponibles dans .NET Framework 3.5, 3.0 SP1 et 2.0 SP1.  
  
## <a name="iri-and-idn-support"></a>Prise en charge des IRI et des IDN  
 Les adresses web sont généralement exprimées à l’aide d’URI (Uniform Resource Identifier) constitués d’un jeu de caractères très limité :  
  
- Lettres ASCII minuscules et majuscules de l’alphabet anglais.  
  
- Chiffres de 0 à 9.  
  
- Un petit nombre d’autres symboles ASCII.  
  
 Les spécifications applicables aux URI sont documentées dans les normes RFC 2396 et RFC 3986 publiées par l’IETF (Internet Engineering Task Force).  
  
 Avec l’essor d’Internet, l’identification de ressources utilisant d’autres langues que l’anglais devient de plus en plus nécessaire. Les identificateurs IRI (International Resource Identifier) sont des identificateurs qui permettent de répondre à ce besoin et d’utiliser des caractères non ASCII (ceux du jeu de caractères Unicode/ISO 10646). Les spécifications applicables aux IRI sont documentées dans la norme RFC 3987 publiée par l’IETF. L’utilisation d’IRI permet l’emploi de caractères Unicode dans les URL.  
  
 La classe <xref:System.Uri?displayProperty=nameWithType> existante a été étendue pour assurer la prise en charge des IRI conformément à la norme RFC 3987. Les utilisateurs actuels ne verront aucun changement dans le comportement de .NET Framework 2.0, sauf s’ils activent spécifiquement les IRI. Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.  
  
 Une application peut spécifier si l’analyse des IDN (Internationalized Domain Name) doit être utilisée pour les noms de domaine et si les règles d’analyse des IRI doivent être appliquées. Cela est spécifié dans le fichier machine.config ou app.config.  
  
 L’activation des IDN entraîne la conversion de toutes les étiquettes Unicode d’un nom de domaine en leurs équivalents Punycode. Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn--. Cela permet de garantir la prise en charge des serveurs DNS existants sur Internet, la plupart d’entre eux prenant uniquement en charge les caractères ASCII (consultez la norme RFC 3940).  
  
 L’activation des IRI et des IDN entraîne une modification de la valeur de la propriété <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>. Cela peut aussi changer le comportement des méthodes <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType> et <xref:System.Uri.IsWellFormedOriginalString%2A>.  
  
 La classe <xref:System.GenericUriParser?displayProperty=nameWithType> a également été étendue pour permettre la création d’un analyseur personnalisable qui prend en charge les IRI et les IDN. Le comportement d’un objet <xref:System.GenericUriParser?displayProperty=nameWithType> est spécifié en passant une combinaison d’opérations au niveau du bit des valeurs disponibles dans l’énumération <xref:System.GenericUriParserOptions?displayProperty=nameWithType> au constructeur <xref:System.GenericUriParser?displayProperty=nameWithType>. Le type <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> indique que l’analyseur prend en charge les règles d’analyse spécifiées dans la norme RFC 3987 pour les IRI (International Resource Identifier). L’utilisation d’IRI nécessite l’activation spécifique de l’analyse des IRI.  
  
 Le type <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> indique que l’analyseur prend en charge l’analyse des IDN pour les noms d’hôte. L’utilisation d’IDN nécessite l’activation spécifique de l’analyse des IDN.  
  
 L’activation de l’analyse des IRI effectue la normalisation et la vérification des caractères selon les dernières règles de la norme RFC 3987 applicables aux IRI. Par défaut, l’analyse des IRI est désactivée, et la normalisation et la vérification des caractères sont effectuées selon les normes RFC 2396 et RFC 3986.  
  
 Le traitement des IRI et des IDN dans la classe <xref:System.Uri?displayProperty=nameWithType> peut également être contrôlé avec les classes de paramètres de configuration <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> et <xref:System.Configuration.IdnElement?displayProperty=nameWithType>. Le paramètre <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> active ou désactive le traitement des IRI dans la classe <xref:System.Uri?displayProperty=nameWithType>. Le paramètre <xref:System.Configuration.IdnElement?displayProperty=nameWithType> active ou désactive le traitement des IDN dans la classe <xref:System.Uri>. Le paramètre <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> contrôle également indirectement les IDN. Le traitement des IRI doit être activé pour permettre le traitement des IDN. Si le traitement des IRI est désactivé, le traitement des IDN est effectué selon le paramètre par défaut (le comportement de .NET Framework 2.0 est utilisé pour la compatibilité et les noms IDN ne sont pas utilisés).  
  
 Le paramètre de configuration pour les classes de configuration <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> et <xref:System.Configuration.IdnElement?displayProperty=nameWithType> est lu une seule fois, au moment de la construction de la première classe <xref:System.Uri?displayProperty=nameWithType>. Les changements apportés ultérieurement aux paramètres de configuration sont ignorés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
