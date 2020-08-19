---
title: Guide de sécurité BinaryFormatter
description: Cet article décrit les risques de sécurité inhérents au type BinaryFormatter et les recommandations pour les différents sérialiseurs à utiliser.
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: ac01fe78c9577563641a8b06a232ed614ed8520a
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558840"
---
# <a name="binaryformatter-security-guide"></a>Guide de sécurité BinaryFormatter

Cet article s’applique aux implémentations .NET suivantes :

* .NET Framework toutes les versions
* .NET Core 2,1-3,1
* .NET 5,0 et versions ultérieures

## <a name="background"></a>Arrière-plan

> [!WARNING]
> Le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type est dangereux et n’est ***pas*** recommandé pour le traitement des données. Les applications doivent cesser `BinaryFormatter` d’utiliser dès que possible, même si elles estiment que les données qu’elles traitent sont dignes de confiance. `BinaryFormatter` la sécurité n’est pas sécurisée.

Cet article s’applique également aux types suivants :

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

Les vulnérabilités de désérialisation sont une catégorie de menace dans laquelle les charges utiles de demande sont traitées de façon non sécurisée. Une personne malveillante qui parvient à exploiter ces vulnérabilités contre une application peut provoquer un déni de service (DoS), la divulgation d’informations ou l’exécution de code à distance dans l’application cible. Cette catégorie de risque rend constamment le [OWASP Top 10](https://owasp.org/www-project-top-ten/). Les cibles incluent des applications écrites dans [différents langages](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data), notamment C/C++, Java et C#.

Dans .NET, la cible de risque la plus importante est celle des applications qui utilisent le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type pour désérialiser les données. `BinaryFormatter` est largement utilisé dans l’écosystème .NET en raison de sa puissance et de sa simplicité d’utilisation. Toutefois, cette même puissance donne aux attaquants la possibilité d’influencer le workflow de contrôle dans l’application cible. Les attaques réussies peuvent empêcher l’attaquant d’exécuter du code dans le contexte du processus cible.

Comme une analogie plus simple, supposez que l’appel de `BinaryFormatter.Deserialize` sur une charge utile est l’équivalent de l’interprétation de cette charge utile comme un exécutable autonome et de son lancement.

## <a name="binaryformatter-security-vulnerabilities"></a>Vulnérabilités de sécurité BinaryFormatter

> [!WARNING]
> La `BinaryFormatter.Deserialize` méthode n’est __jamais__ sûre quand elle est utilisée avec une entrée non fiable. Nous recommandons vivement aux consommateurs d’utiliser l’une des solutions décrites plus loin dans cet article.

`BinaryFormatter` a été implémenté avant que les vulnérabilités de désérialisation étaient une catégorie de menace bien comprise. Par conséquent, le code ne suit pas les meilleures pratiques modernes. La `Deserialize` méthode peut être utilisée comme un vecteur pour permettre aux attaquants d’effectuer des attaques dos contre les applications consommatrices. Ces attaques peuvent rendre l’application inactive ou entraîner un arrêt inattendu du processus. Cette catégorie d’attaque ne peut pas être atténuée avec un `SerializationBinder` ou tout autre `BinaryFormatter` commutateur de configuration. .NET considère ce comportement comme étant de la ***conception*** et n’émet pas de mise à jour de code pour modifier le comportement.

`BinaryFormatter.Deserialize` peut être vulnérable à d’autres catégories d’attaques, telles que la divulgation d’informations ou l’exécution de code à distance. L’utilisation de fonctionnalités telles qu’un personnalisé <xref:System.Runtime.Serialization.SerializationBinder> est peut-être insuffisante pour atténuer correctement ces risques. Il est possible qu’une nouvelle vulnérabilité soit découverte pour laquelle .NET ne peut pratiquement pas publier une mise à jour de sécurité. Les consommateurs doivent évaluer leurs scénarios individuels et prendre en compte leur exposition potentielle à ces risques.

Nous recommandons `BinaryFormatter` aux consommateurs d’effectuer des évaluations des risques individuels sur leurs applications. La seule responsabilité du consommateur est de déterminer s’il faut utiliser `BinaryFormatter` . Les consommateurs doivent évaluer les exigences de sécurité, techniques, de réputation, juridiques et réglementaires de l’utilisation de `BinaryFormatter` .

## <a name="preferred-alternatives"></a>Alternatives recommandées

.NET propose plusieurs sérialiseurs intégrés qui peuvent gérer en toute sécurité les données non approuvées :

* <xref:System.Xml.Serialization.XmlSerializer> et <xref:System.Runtime.Serialization.DataContractSerializer> pour sérialiser des graphiques d’objets dans et à partir de XML. Ne confondez pas `DataContractSerializer` avec  <xref:System.Runtime.Serialization.NetDataContractSerializer> .
* <xref:System.IO.BinaryReader> et <xref:System.IO.BinaryWriter> for XML et JSON.
* Les <xref:System.Text.Json> API pour sérialiser des graphiques d’objets dans JSON.

## <a name="dangerous-alternatives"></a>Alternatives dangereuses

Évitez les sérialiseurs suivants :

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

Les sérialiseurs précédents effectuent tous une désérialisation polymorphe non restreinte et sont dangereux, tout comme `BinaryFormatter` .

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>Les risques liés à l’hypothèse que les données sont dignes de confiance

Souvent, un développeur d’applications peut croire qu’il ne traite que des entrées approuvées. Le cas d’entrée sécurisée est vrai dans certains cas rares. Mais il est bien plus courant qu’une charge utile franchit une limite d’approbation sans que le développeur ne la rende compte.

Prenons l’exemple d' __un serveur local sur__ lequel les employés utilisent un client de bureau à partir de leurs stations de travail pour interagir avec le service. Ce scénario peut être considéré naïvement comme une configuration « sûre » où l’utilisation de `BinaryFormatter` est acceptable. Toutefois, ce scénario présente un vecteur pour les programmes malveillants qui ont accès à l’ordinateur d’un seul employé pour pouvoir se répandre au sein de l’entreprise. Ce programme malveillant peut tirer parti de l’utilisation par l’entreprise de `BinaryFormatter` pour passer de la station de travail de l’employé au serveur principal. Il peut ensuite exfiltrer les données sensibles de l’entreprise. Ces données peuvent inclure des secrets commerciaux ou des données client.

__Envisagez également une application qui utilise `BinaryFormatter` pour conserver l’état de l’enregistrement.__ Cela peut sembler un scénario sûr, car la lecture et l’écriture de données sur votre propre disque dur représentent une menace mineure. Toutefois, le partage de documents entre courrier électronique ou Internet est courant, et la plupart des utilisateurs finaux ne percevront pas l’ouverture de ces fichiers téléchargés comme un comportement risqué.

Ce scénario peut être exploité en être mal intentionné effet. Si l’application est un jeu, les utilisateurs qui partagent des fichiers sont placés à l’insu. Les développeurs peuvent également être ciblés. L’attaquant peut envoyer un message électronique au support technique des développeurs, en joignant un fichier de données malveillantes et en demandant à l’équipe du support technique de l’ouvrir. Ce type d’attaque peut entraîner une brèche dans l’entreprise.

Un autre scénario est l’emplacement où le fichier de données est stocké dans le stockage cloud et synchronisé automatiquement entre les ordinateurs de l’utilisateur. Une personne malveillante qui parvient à accéder au compte de stockage cloud peut corrompre le fichier de données. Ce fichier de données sera automatiquement synchronisé avec les ordinateurs de l’utilisateur. La prochaine fois que l’utilisateur ouvrira le fichier de données, la charge utile de l’attaquant s’exécutera. Par conséquent, l’attaquant peut exploiter un compte de stockage cloud compromis pour obtenir des autorisations d’exécution de code complètes.

__Prenons l’exemple d’une application qui passe d’un modèle d’installation de bureau à un modèle basé sur le Cloud.__ Ce scénario comprend des applications qui se déplacent d’une application de bureau ou d’un modèle de client riche dans un modèle basé sur le Web. Les modèles de menace dessinés pour l’application de bureau ne sont pas nécessairement applicables au service Cloud. Le modèle de menace pour l’application de bureau peut ignorer une menace donnée comme « non intéressant pour le client à attaquer lui-même ». Toutefois, cette même menace peut devenir intéressante lorsqu’elle considère qu’un utilisateur distant (le client) attaque le service Cloud lui-même.

> [!NOTE]
> En général, l’objectif de la sérialisation est de transmettre un objet à l’intérieur ou à l’extérieur d’une application. Un exercice de modélisation des menaces marque presque toujours ce type de transfert de données comme traversant une limite d’approbation.

## <a name="further-resources"></a>Ressources supplémentaires

* [YSoSerial.net](https://github.com/pwntester/ysoserial.net) pour la recherche de la manière dont les adversaires attaquent les applications qui utilisent `BinaryFormatter` .
* Informations générales sur les vulnérabilités de désérialisation :
  * [OWASP Top 10-A8:2017-désérialisation non sécurisée](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502 : désérialisation des données non approuvées](https://cwe.mitre.org/data/definitions/502.html)
