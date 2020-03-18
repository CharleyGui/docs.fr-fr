---
title: Sécurité LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 5b7eb815b058cba008f1db2cf683c8934c19b743
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73423375"
---
# <a name="linq-to-xml-security-c"></a>Sécurité LINQ to XML (C#)
Cette rubrique décrit les problèmes de sécurité associés à LINQ to XML. De plus, elle fournit quelques conseils pour réduire l'exposition aux risques de sécurité.  
  
## <a name="linq-to-xml-security-overview"></a>Vue d'ensemble de la sécurité LINQ to XML  
 LINQ to XML est conçu plus à des fins de commodité de programmation que pour les applications côté serveur présentant des exigences de sécurité strictes. La plupart des scénarios XML impliquent le traitement de documents XML approuvés plutôt que le traitement de documents XML non approuvés chargés sur un serveur. LINQ to XML est optimisé pour ces scénarios.  
  
 Si vous devez traiter des données non approuvées provenant de sources inconnues, Microsoft vous recommande d'utiliser une instance de la classe <xref:System.Xml.XmlReader> qui a été configurée pour filtrer les attaques par déni de service XML connues.  
  
 Si vous avez configuré un objet <xref:System.Xml.XmlReader> pour limiter les attaques par déni de service, vous pouvez utiliser ce lecteur pour remplir une arborescence LINQ to XML tout en continuant de tirer parti des améliorations de productivité de programmeur offertes par LINQ to XML. De nombreuses techniques d'atténuation des risques nécessitent la création de lecteurs configurés pour limiter le problème de sécurité, puis l'instanciation d'une arborescence XML par le biais du lecteur configuré.  
  
 Le langage XML est intrinsèquement vulnérable aux attaques par déni de service car les documents ne sont pas limités en termes de taille, de profondeur, de taille de nom d'élément, et ainsi de suite. Quel que soit le composant que vous utilisez pour traiter le code XML, vous devez toujours être prêt à recycler le domaine d'application s'il utilise des ressources excessives.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Atténuation des attaques XML, XSD, XPath et XSLT  
 LINQ to XML est basé sur les objets <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>. LINQ to XML prend en charge XSD et XPath via les méthodes d'extension dans les espaces de noms <xref:System.Xml.Schema?displayProperty=nameWithType> et <xref:System.Xml.XPath?displayProperty=nameWithType>. L'utilisation des classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator> et <xref:System.Xml.XmlWriter> avec LINQ to XML vous permet d'appeler XSLT pour transformer des arborescences XML.  
  
 Si vous opérez dans un environnement moins sécurisé, plusieurs problèmes de sécurité sont associés au langage XML et à l'utilisation des classes dans <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType> et <xref:System.Xml.Xsl?displayProperty=nameWithType>. Ces problèmes incluent, entre autres, les suivants :  
  
- XSD, Xpath et XSLT sont des langages basés sur des chaînes dans lesquels vous spécifiez des opérations qui consomment beaucoup de temps ou de mémoire. Il incombe aux programmeurs d'applications qui prennent des chaînes XSD, XPath ou XSLT à partir de sources non approuvées de confirmer que ces chaînes ne sont pas malveillantes ou de contrôler et de limiter le risque que l'évaluation de ces chaînes n'entraîne une consommation excessive de ressources système.  
  
- Les schémas XSD (y compris les schémas en ligne), sont par nature vulnérables aux attaques par déni de service ; vous ne devez pas accepter de schémas provenant de sources non approuvées.  
  
- XSD et XSLT peuvent inclure des références à d'autres fichiers, et ces références peuvent entraîner des attaques inter-zones ou inter-domaines.  
  
- Les entités externes dans les DTD peuvent entraîner des attaques inter-zones ou inter-domaines.  
  
- Les DTD sont vulnérables aux attaques par déni de service.  
  
- Les documents XML extrêmement profonds peuvent présenter des risques de déni de service ; il peut être préférable de limiter la profondeur des documents XML.  
  
- N'acceptez pas de composants de prise en charge, tels que des objets <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager> et <xref:System.Xml.XmlResolver>, provenant d'assemblys non approuvés.  
  
- Lisez les données en bloc afin de limiter les risques d'attaques sur les grands documents.  
  
- Les blocs de scripts dans des feuilles de style XSLT peuvent donner lieu à de nombreuses attaques.  
  
- Effectuez une validation soigneuse avant de construire des expressions XPath dynamiques.  
  
## <a name="linq-to-xml-security-issues"></a>Problèmes de sécurité liés à LINQ to XML  
 Les problèmes de sécurité mentionnés dans cette rubrique ne sont pas présentés dans un ordre particulier. Tous ces problèmes sont importants et doivent être traités en conséquence.  
  
 Une attaque par élévation de privilège réussie procure à un assembly malveillant davantage de contrôle sur son environnement. Une attaque par élévation de privilège réussie peut entraîner une divulgation des données, un déni de service et plus encore.  
  
 Les applications ne doivent pas divulguer de données aux utilisateurs non autorisés à afficher ces données.  
  
 Les attaques par déni de service font en sorte que l'analyseur XML ou LINQ to XML consomment des quantités de mémoire ou un temps processeur excessifs. Les attaques par déni de service sont considérés comme étant moins graves que les attaques par élévation de privilège ou les attaques par divulgation de données. Elles sont néanmoins importantes dans un scénario dans lequel un serveur doit traiter des documents XML provenant de sources non approuvées.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Les exceptions et messages d'erreur peuvent révéler des données  
 La description d'une erreur peut révéler des données, par exemple les données transformées, des noms de fichiers ou des détails d'implémentation. Les messages d'erreur ne doivent pas être exposés aux appelants qui ne sont pas approuvés. Vous devez intercepter toutes les erreurs et les signaler avec vos propres messages d'erreur personnalisés.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>N'appelez pas CodeAccessPermissions.Assert dans un gestionnaire d'événements  
 Un assembly peut avoir des autorisations inférieures ou supérieures. Un assembly qui a des autorisations supérieures dispose d'un meilleur contrôle sur l'ordinateur et ses environnements.  
  
 Si du code dans un assembly disposant d'autorisations supérieures appelle <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> dans un gestionnaire d'événements et que l'arborescence XML est ensuite passée à un assembly malveillant disposant d'autorisations limitées, l'assembly malveillant peut provoquer le déclenchement d'un événement. Étant donné que l'événement exécute du code qui se trouve dans un assembly disposant d'autorisations supérieures, l'assembly malveillant opérerait alors avec des privilèges élevés.  
  
 Microsoft recommande de ne jamais appeler <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> dans un gestionnaire d'événements.  
  
### <a name="dtds-are-not-secure"></a>Les DTD ne sont pas sécurisés  
 Les entités dans les DTD, par nature, ne sont pas sécurisées. Il est possible qu'un document XML malveillant contenant un DTD oblige l'analyseur à utiliser toute la mémoire et le temps processeur, ce qui constitue une attaque par déni de service. Par conséquent, dans LINQ to XML, le traitement des DTD est désactivé par défaut. Vous ne devez pas accepter de DTD provenant de sources non approuvées.  
  
 L'un des exemples de l'acceptation de DTD provenant de sources non approuvées est une application Web qui autorise les utilisateurs Web à télécharger un fichier XML qui fait référence à un DTD et un fichier DTD. Lors de la validation du fichier, un DTD malveillant pourrait déclencher une attaque par déni de service sur votre serveur. Un autre exemple consiste à faire référence à un DTD sur un partage réseau qui autorise également l'accès FTP anonyme.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Évitez l'allocation de mémoire tampon excessive  
 Les développeurs d'applications doivent savoir que les sources de données extrêmement volumineuses peuvent entraîner un épuisement des ressources et des attaques par déni de service.  
  
 Si un utilisateur malveillant soumet ou télécharge un très grand document XML, il pourrait utiliser LINQ to XML pour consommer des ressources système excessives. Cela peut constituer une attaque par déni de service. Pour éviter ce problème, vous pouvez définir la propriété <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> et créer un lecteur limité quant à la taille des documents qu'il peut charger. Vous utilisez ensuite le lecteur pour créer l'arborescence XML.  
  
 Par exemple, si vous savez que la taille maximale attendue de vos documents XML provenant d'une source non approuvée sera inférieure à 50 Ko, affectez à la propriété <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> la valeur 100 000. Cela ne gênera pas le traitement de vos documents XML mais atténuera les menaces d'attaques par déni de service dans lesquelles des documents téléchargés pourraient consommer de grandes quantités de mémoire.  
  
### <a name="avoid-excess-entity-expansion"></a>Évitez l'extension d'entité excessive  
 L'une des attaques par déni de service connues en cas d'utilisation d'un DTD est un document qui provoque une extension d'entité excessive. Pour éviter ce problème, vous pouvez définir la propriété <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> et créer un lecteur limité quant au nombre de caractères résultant de l'extension d'entité. Vous utilisez ensuite le lecteur pour créer l'arborescence XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Limitez la profondeur de la hiérarchie XML  
 Une attaque par déni de service peut également se produire lorsqu'un document soumis possède une profondeur de hiérarchie excessive. Pour éviter ce problème, vous pouvez encapsuler un objet <xref:System.Xml.XmlReader> dans votre propre classe qui compte la profondeur d'éléments. Si la profondeur dépasse un niveau raisonnable prédéterminé, vous pouvez terminer le traitement du document malveillant.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Protégez-vous contre les implémentations XmlReader ou XmlWriter non approuvées  
 Les administrateurs doivent vérifier que toute implémentation <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> fournie par une source externe possède des noms forts et a été inscrite dans la configuration de l'ordinateur. Cela empêche le chargement de tout code malveillant se faisant passer pour un lecteur ou un writer.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Libérez périodiquement les objets qui font référence à XName  
 Pour se protéger contre certains types d'attaques, les programmeurs d'applications doivent libérer régulièrement tous les objets qui font référence à un objet <xref:System.Xml.Linq.XName> dans le domaine d'application.  
  
### <a name="protect-against-random-xml-names"></a>Protégez-vous contre les noms XML aléatoires  
 Les applications qui prennent des données de sources non approuvées doivent considérer l'utilisation d'un objet <xref:System.Xml.XmlReader> encapsulé dans du code personnalisé afin d'étudier la présence éventuelle de noms et d'espaces de noms XML aléatoires. En cas de détection de noms et d'espaces de noms XML aléatoires, l'application peut alors terminer le traitement du document malveillant.  
  
 Vous souhaiterez peut-être limiter la quantité de noms dans tout espace de noms donné (y compris les noms qui n'appartiennent à aucun espace de noms) à un niveau raisonnable.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Les annotations sont accessibles aux composants logiciels qui partagent une arborescence LINQ to XML  
 LINQ to XML peut être utilisé pour générer des pipelines de traitement dans lesquels différents composants d'applications chargent, valident, interrogent, transforment, mettent à jour et enregistrent des données XML qui sont passées d'un composant à un autre en tant qu'arborescences XML. Cela peut aider à optimiser les performances car le traitement lié au chargement et à la sérialisation des objets en texte XML n'est effectué qu'aux extrémités du pipeline. Les développeurs doivent cependant savoir que toutes les annotations et gestionnaires d'événements créés par un composant sont accessibles aux autres composants. Cela peut créer un certain nombre de vulnérabilités si les composants ont différents niveaux de confiance. Pour générer des pipelines sécurisés entre des composants à faible approbation, vous devez sérialiser les objets LINQ to XML en texte XML avant de passer les données à un composant non approuvé.  
  
 Une certaine sécurité est fournie par le Common Language Runtime (CLR). Par exemple, un composant qui n'inclut pas une classe privée ne peut pas accéder aux annotations entrées par cette classe. Toutefois, les annotations peuvent être supprimées par les composants qui ne peuvent pas les lire. Cela pourrait être utilisée pour provoquer une attaque de falsification.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation (LINQ to XML) (C#)](linq-to-xml-overview.md)
