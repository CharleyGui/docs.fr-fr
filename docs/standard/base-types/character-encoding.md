---
title: Encodage de caractères dans .NET
description: Découvrez plus en détail l’encodage et le décodage de caractères dans .NET.
ms.date: 12/22/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
ms.openlocfilehash: 3cd461d8c56c3f31bf3ffe04acf239ecd32fe328
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711439"
---
# <a name="character-encoding-in-net"></a>Encodage de caractères dans .NET

Les caractères sont des entités abstraites qui peuvent être représentées de nombreuses façons différentes. Un encodage de caractères est un système qui associe chaque caractère d'un jeu de caractères pris en charge à une valeur qui représente ce caractère. Par exemple, le code Morse est un encodage de caractères qui associe chaque caractère de l'alphabet latin à une séquence de points et de tirets qui conviennent pour la transmission sur des lignes télégraphiques. Un encodage de caractères pour les ordinateurs associe chaque caractère d'un jeu de caractères à une valeur numérique qui représente ce caractère. Un encodage de caractères a deux composants distincts :

- Un encodeur, qui convertit une séquence de caractères en une séquence de valeurs numériques (octets).

- Un décodeur, qui convertit une séquence d'octets en une séquence de caractères.

L'encodage de caractères décrit les règles selon lesquelles un encodeur et un décodeur fonctionnent. Par exemple, la classe <xref:System.Text.UTF8Encoding> décrit les règles d'encodage et de décodage d'UTF-8, qui utilise de un à quatre octets pour représenter un caractère Unicode. L'encodage et le décodage peuvent également inclure une validation. Par exemple, la classe <xref:System.Text.UnicodeEncoding> vérifie tous les substituts afin de vérifier qu'ils constituent des paires de substitution valide. (Une paire de substitution se compose d’un personnage avec un point de code qui va de U-D800 à U-DBFF suivie d’un personnage avec un point de code qui va de U-DC00 à U-DFFF.)  Une stratégie de repli détermine comment un encoder gère les caractères invalides ou comment un décodeur gère les octets invalides.

> [!WARNING]
> Les classes d’encodage .NET permettent de stocker et de convertir les données caractères. Elles ne doivent pas utilisées pour stocker des données binaires sous forme de chaîne. En fonction de l'encodage utilisé, la conversion de données binaires en un format chaîne avec les classes d'encodage peut entraîner un comportement inattendu et produire des données incorrectes ou endommagées. Pour convertir des données binaires en chaîne, utilisez la méthode <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> .

.NET utilise l’encodage UTF-16 (représenté par la classe <xref:System.Text.UnicodeEncoding>) pour représenter des caractères et des chaînes. Les applications qui ciblent le common language runtime utilisent des encodeurs pour mapper les représentations de caractères Unicode prises en charge par le common language runtime à d'autres schémas de codage. Elles utilisent des décodeurs pour mapper les caractères des encodages non-Unicode à Unicode.

Cette rubrique contient les sections suivantes :

- [Encodages dans .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)

- [Sélection d'une classe d'encodage](../../../docs/standard/base-types/character-encoding.md#Selecting)

- [Utilisation d'un objet d'encodage](../../../docs/standard/base-types/character-encoding.md#Using)

- [Choix d'une stratégie de secours](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)

- [Implementing a Custom Fallback Strategy](../../../docs/standard/base-types/character-encoding.md#Custom)

<a name="Encodings"></a>

## <a name="encodings-in-net"></a>Encodages dans .NET

Toutes les classes d'encodage de caractères de .NET héritent de la classe <xref:System.Text.Encoding?displayProperty=nameWithType>, qui est une classe abstraite définissant les fonctionnalités communes à tous les encodages de caractères. Pour accéder aux objets d’encodage individuels implémentés dans .NET, procédez comme suit :

- Utilisez les propriétés statiques de la classe <xref:System.Text.Encoding>, qui retournent des objets représentant les encodages de caractères standard disponibles dans .NET (ASCII, UTF-7, UTF-8, UTF-16 et UTF-32). Par exemple, la propriété <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> retourne un objet <xref:System.Text.UnicodeEncoding> . Chaque objet utilise la stratégie de secours pour les remplacements pour traiter les chaînes qu'il ne peut pas encoder et les octets qu'il ne peut pas décoder. (Pour plus d’informations, consultez la section [Remplacement Fallback.)](../../../docs/standard/base-types/character-encoding.md#Replacement)

- Appelez le constructeur de classe de l'encodage. Les objets pour les encodages ASCII, UTF-7, UTF-8, UTF-16 et UTF-32 peuvent être instanciés de cette façon. Par défaut, chaque objet utilise la stratégie de secours pour les remplacements pour traiter les chaînes qu'il ne peut pas encoder et les octets qu'il ne peut pas décoder, mais vous pouvez spécifier qu'au lieu de cela, une exception doit être levée. (Pour plus d’informations, consultez les sections [Replacement Fallback](../../../docs/standard/base-types/character-encoding.md#Replacement) et [Exception Fallback](../../../docs/standard/base-types/character-encoding.md#Exception) .)

- Appelez le constructeur <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> et passez-lui un entier qui représente l'encodage. Les objets d'encodage standard utilisent la stratégie de secours pour les remplacements. Les objets d'encodage de page de codes et de jeu de caractères codés sur deux octets (DBCS) utilisent la stratégie de secours la mieux adaptée pour traiter les chaînes qu'ils ne peuvent pas encoder et les octets qu'ils ne peuvent pas décoder. (Pour plus d’informations, consultez la section [Best-Fit Fallback](../../../docs/standard/base-types/character-encoding.md#BestFit) .)

- Appelez la méthode <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>, qui retourne les encodages standard, de page de codes ou DBCS disponibles dans .NET. Les surcharges vous permettent de spécifier un objet de secours pour l'encodeur et pour le décodeur.

> [!NOTE]
> La norme Unicode affecte un point de code (un nombre) et un nom à chaque caractère de chaque jeu de caractères pris en charge. Par exemple, le caractère "A" est représenté par le point de code U+0041 et par le nom "LETTRE MAJUSCULE LATINE A". Les encodages UTF (Unicode Transformation Format) définissent des moyens d'encoder ce point de code en une séquence d'un ou plusieurs octets. Un schéma d'encodage Unicode simplifie le développement d'applications mondialisées, car il permet la représentation avec un encodage unique des caractères provenant de n'importe quel jeu de caractères. Les développeurs d'applications ne doivent plus faire le suivi du schéma d'encodage qui a été utilisé pour produire des caractères pour une langue ou un système d'écriture spécifique, et les données peuvent être partagées entre des systèmes à une échelle internationale sans risque d'endommagement.
>
> .NET prend en charge trois encodages définis par la norme Unicode : UTF-8, UTF-16 et UTF-32. Pour plus d’informations, consultez la norme Unicode dans la [page d’accueil Unicode](https://www.unicode.org/).

Vous pouvez récupérer des informations sur les encodages disponibles dans .NET en appelant la méthode <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType>. .NET prend en charge les systèmes d’encodage de caractères répertoriés dans le tableau suivant.

|Encodage|Classe|Description|Avantages et inconvénients|
|--------------|-----------|-----------------|-------------------------------|
|ASCII|<xref:System.Text.ASCIIEncoding>|Encode une plage de caractères limitée en utilisant les sept bits de poids le plus faible d'un octet.|Étant donné que cet encodage prend en charge seulement des valeurs de caractère de U+0000 à U+007F, dans la plupart des cas, il ne convient pas aux applications internationalisées.|
|UTF-7|<xref:System.Text.UTF7Encoding>|Représente les caractères sous forme de séquences de caractères ASCII sur 7 bits. Les caractères Unicode non-ASCII sont représentés par une séquence d'échappement de caractères ASCII.|UTF-7 prend en charge les protocoles de messagerie et les protocoles de groupe de discussion. UTF-7 n'est cependant pas particulièrement sécurisé ou robuste. Dans certains cas, la modification d'un seul bit peut changer radicalement l'interprétation de toute une chaîne UTF-7. Dans d'autres cas, des chaînes UTF-7 différentes peuvent correspondre à l'encodage d'un même texte. Pour les séquences incluant des caractères non-ASCII, UTF-7 nécessite davantage d'espace qu'UTF-8, et l'encodage/décodage est plus lent. Par conséquent, il est préférable d'utiliser UTF-8 au lieu d'UTF-7 si c'est possible.|
|UTF-8|<xref:System.Text.UTF8Encoding>|Représente chaque point de code Unicode sous la forme d'une séquence de un à quatre octets.|UTF-8 prend en charge des tailles de données de 8 bits et fonctionne bien avec de nombreux systèmes d'exploitation. Pour la plage de caractères ASCII, UTF-8 est identique à l'encodage ASCII et permet un ensemble de caractères plus large. Cependant, pour les jeux de caractères Chinois-Japonais-Coréen (CJC), UTF-8 peut nécessiter trois octets pour chaque caractère et aboutir potentiellement à des tailles de données supérieures à celles d'UTF-16. Notez que parfois, la quantité de données ASCII, comme des balises HTML, justifie l'augmentation de la taille pour les jeux de caractères CJC.|
|UTF-16|<xref:System.Text.UnicodeEncoding>|Représente chaque point de code Unicode sous la forme d'une séquence de un ou deux entiers sur 16 bits. La plupart des caractères Unicode courants ne nécessitent qu'un seul point de code UTF-16, tandis que les caractères Unicode additionnels (U+10000 et supérieurs) nécessitent deux points de code de substitution UTF-16. Les ordres des octets Little Endian et Big Endian sont pris en charge.|L'encodage UTF-16 est utilisé par le common language runtime pour représenter les valeurs <xref:System.Char> et <xref:System.String> , et il est utilisé par le système d'exploitation Windows pour représenter les `WCHAR` .|
|UTF-32|<xref:System.Text.UTF32Encoding>|Représente chaque point de code Unicode sous la forme d'un entier 32 bits. Les ordres des octets Little Endian et Big Endian sont pris en charge.|L'encodage UTF-32 est utilisé quand les applications ne doivent pas avoir le comportement du point de code de substitution de l'encodage UTF-16 sur les systèmes d'exploitation pour lesquels l'espace encodé est trop important. Les glyphes uniques restitués à l'affichage peuvent néanmoins encore être encodés avec plusieurs caractères UTF-32.|
|Encodages ANSI/ISO||Prend en charge différentes pages de codes. Sur les systèmes d'exploitation Windows, les pages de codes sont utilisées pour prendre en charge une langue spécifique ou un groupe de langues spécifique. Pour un tableau répertoriant les pages de codes prises en charge par .NET, consultez la classe <xref:System.Text.Encoding>. Vous pouvez récupérer un objet d'encodage pour une page de codes spécifique en appelant la méthode <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> .|Une page de codes contient 256 points de code et commence à zéro. Dans la plupart des pages de codes, les points de code de 0 à 127 représentent le jeu de caractères ASCII, et les points de code de 128 à 255 diffèrent considérablement entre les pages de code. Par exemple, la page de codes 1252 fournit les caractères pour les systèmes d'écriture latins, y compris l'anglais, l'allemand et le français. Les derniers 128 points de code de la page de codes 1252 contiennent les caractères accentués. La page de codes 1253 fournit les codes des caractères qui sont requis dans le système d'écriture grec. Les derniers 128 points de code de la page de codes 1253 contiennent les caractères grecs. Par conséquent, une application qui s'appuie sur les pages de codes ANSI ne peut pas stocker le grec et l'allemand dans le même flux de texte, sauf si elle inclut un identificateur indiquant la page de codes référencée.|
|Encodages DBCS (Double-Byte Character Set, Jeu de caractères codés sur deux octets)||Prend en charge des langues comme le chinois, le japonais et le coréen, qui contiennent plus de 256 caractères. Dans un jeu de caractères DBCS, une paire de points de code (un double octet) représente chaque caractère. La propriété <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> retourne `false` pour les encodages DBCS. Vous pouvez récupérer un objet d'encodage pour un jeu de caractères DBCS spécifique en appelant la méthode <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> .|Dans un jeu de caractères DBCS, une paire de points de code (un double octet) représente chaque caractère. Quand une application traite des données DBCS, le premier octet d'un caractère DBCS (l'octet de tête) est traité en combinaison avec l'octet de fin qui le suit immédiatement. Comme une seule paire de points de code sur un double octet peut représenter des caractères différents en fonction de la page de codes, ce schéma ne permet pas non plus la combinaison de deux langues, comme le japonais et le chinois, dans le même flux de données.|

Ces encodages vous permettent de travailler avec des caractères Unicode ainsi qu'avec les encodages les plus couramment utilisés dans les applications héritées. En outre, vous pouvez créer un encodage personnalisé en définissant une classe qui dérive de <xref:System.Text.Encoding> et en remplaçant ses membres.

### <a name="platform-notes-net-core"></a>Notes sur les plateformes : .NET Core

Par défaut, .NET Core ne met à disposition aucune page de codes autre que la page de codes 28591 et les encodages Unicode, comme UTF-8 et UTF-16. Vous pouvez cependant ajouter à votre application les encodages des pages de code qui se trouvent dans les applications Windows standard ciblant .NET. Pour des informations complètes, consultez la rubrique <xref:System.Text.CodePagesEncodingProvider> .

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Sélection d'une classe d'encodage

Si vous avez la possibilité de choisir l'encodage à utiliser par votre application, utilisez un encodage Unicode, de préférence <xref:System.Text.UTF8Encoding> ou <xref:System.Text.UnicodeEncoding>. (.NET prend également en charge un troisième encodage Unicode, <xref:System.Text.UTF32Encoding>.)

Si vous envisagez d'utiliser un encodage ASCII (<xref:System.Text.ASCIIEncoding>), choisissez <xref:System.Text.UTF8Encoding> à la place. Les deux encodages sont identiques pour le jeu de caractères ASCII, mais <xref:System.Text.UTF8Encoding> présente les avantages suivants :

- Il peut représenter tous les caractères Unicode, alors que <xref:System.Text.ASCIIEncoding> prend en charge seulement les valeurs des caractères Unicode entre U+0000 et U+007F.

- Il offre une fonction de détection d'erreur et une meilleure sécurité.

- Il a été optimisé pour être aussi rapide que possible et il doit normalement être plus rapide n'importe quel autre encodage. Même pour du contenu qui est entièrement en ASCII, les opérations effectuées avec <xref:System.Text.UTF8Encoding> sont plus rapides que les opérations effectuées avec <xref:System.Text.ASCIIEncoding>.

Vous devez envisager d'utiliser <xref:System.Text.ASCIIEncoding> seulement pour les applications héritées. Cependant, même pour les applications héritées, <xref:System.Text.UTF8Encoding> peut être un meilleur choix pour les raisons suivantes (en supposant que les paramètres par défaut sont utilisés) :

- Si votre application a du contenu qui n'est pas strictement ASCII et qu'elle l'encode avec <xref:System.Text.ASCIIEncoding>, chaque caractère non-ASCII est encodé sous la forme d'un point d'interrogation (?). Si l'application décode ensuite ces données, les informations sont perdues.

- Si votre application a du contenu qui n'est pas strictement ASCII et qu'elle l'encode avec <xref:System.Text.UTF8Encoding>, le résultat paraît inintelligible s'il est interprété comme étant en ASCII. Cependant, si l'application utilise ensuite un décodeur UTF-8 pour décoder ces données, les données apparaissent à nouveau correctes.

Dans une application web, les caractères envoyés au client en réponse à une demande web doivent refléter l'encodage utilisé sur le client. Dans la plupart des cas, vous devez définir la propriété <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> à la valeur retournée par la propriété <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> pour afficher le texte dans le encodage attendu par l'utilisateur.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Utilisation d'un objet d'encodage

Un encodeur convertit une chaîne de caractères (le plus souvent, des caractères Unicode) en son équivalent numérique (en octets). Par exemple, vous pouvez utiliser un encodeur ASCII pour convertir des caractères Unicode en ASCII, pour pouvoir les afficher sur la console. Pour effectuer la conversion, vous appelez la méthode <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> . Si vous voulez déterminer le nombre d'octets nécessaires pour stocker les caractères encodés avant de procéder à l'encodage, vous pouvez appeler la méthode <xref:System.Text.Encoding.GetByteCount%2A> .

L'exemple suivant utilise un tableau d'octets seuls pour encoder des chaînes dans deux opérations distinctes. Il gère un index qui indique la position de départ dans le tableau d'octets pour l'ensemble suivant d'octets encodés en ASCII. Il appelle la méthode <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> pour vérifier que le tableau d'octets est assez grand pour contenir la chaîne encodée. Il appelle ensuite la méthode <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> pour encoder les caractères de la chaîne.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Un décodeur convertit un tableau d'octets qui reflète un encodage de caractères spécifique en un jeu de caractères dans un tableau de caractères ou dans une chaîne. Pour décoder un tableau d'octets en un tableau de caractères, vous appelez la méthode <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> . Pour décoder un tableau d'octets en un tableau de caractères, vous appelez la méthode <xref:System.Text.Encoding.GetString%2A> . Si vous voulez déterminer le nombre d'octets nécessaires pour stocker les caractères décodés avant de procéder au décodage, vous pouvez appeler la méthode <xref:System.Text.Encoding.GetCharCount%2A> .

L'exemple suivant encode trois chaînes, puis les décode dans un même tableau de caractères. Il gère un index qui indique la position de départ dans le tableau de caractères pour l'ensemble suivant de caractères décodés. Il appelle la méthode <xref:System.Text.ASCIIEncoding.GetCharCount%2A> pour vérifier que le tableau de caractères est assez grand pour contenir les caractères décodés. Il appelle ensuite la méthode <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> pour décoder le tableau d'octets.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Les méthodes d'encodage et de décodage d'une classe dérivée de <xref:System.Text.Encoding> sont conçues pour fonctionner sur un ensemble de données complet ; autrement dit, toutes les données à encoder ou à décoder sont fournies dans un seul appel de méthode. Cependant, dans certains cas, les données sont disponibles dans un flux, et les données à encoder ou à décoder peuvent être disponibles seulement via des opérations de lecture distinctes. Ceci nécessite la conservation par l'opération d'encodage ou de décodage des états enregistrés depuis son précédent appel. Les méthodes des classes dérivées de <xref:System.Text.Encoder> et de <xref:System.Text.Decoder> sont capables de traiter les opérations de codage et de décodage qui recouvrent plusieurs appels de méthode.

Un objet <xref:System.Text.Encoder> pour un encodage particulier est disponible auprès de la propriété <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> de cet encodage. Un objet <xref:System.Text.Decoder> pour un encodage particulier est disponible auprès de la propriété <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> de cet encodage. Pour les opérations de décodage, notez que les classes dérivées de <xref:System.Text.Decoder> incluent une méthode <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> , mais qu'elles n'ont pas de méthode correspondant à <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.

L'exemple suivant montre la différence entre l'utilisation des méthodes <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> et <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> pour le décodage d'un tableau d'octets Unicode. L'exemple encode une chaîne qui contient des caractères Unicode vers un fichier, puis utilise les deux méthodes de décodage pour les décoder par dix octets à la fois. Une paire de substitution se trouvant dans les dixième et onzième octets, elle est décodée dans des appels de méthode distincts. Comme la sortie le montre, la méthode <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> ne peut pas décoder correctement les octets et les remplace par U+FFFD (CARACTÈRE DE REMPLACEMENT). En revanche, la méthode <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> peut décoder correctement le tableau d'octets pour obtenir la chaîne d'origine.

[!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
[!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]

<a name="FallbackStrategy"></a>

## <a name="choosing-a-fallback-strategy"></a>Choix d'une stratégie de secours

Quand une méthode tente d'encoder ou de décoder un caractère, mais qu'il n'existe pas de mappage, elle doit implémenter une stratégie de secours qui détermine comment l'échec du mappage doit être traité. Il existe trois types de stratégies de secours :

- Best-Fit Fallback

- Stratégie de secours pour les remplacements

- Exception Fallback

> [!IMPORTANT]
> Les problèmes les plus courants des opérations d'encodage se produisent quand un caractère Unicode ne peut pas être mappé à un encodage de page de codes particulier. Les problèmes les plus courants des opérations de décodage se produisent quand des séquences d'octets non valides ne peut pas être traduites en caractères Unicode valides. Pour ces raisons, vous devez savoir quelle stratégie de secours est utilisée par un objet de codage particulier. Chaque fois que c'est possible, vous devez spécifier la stratégie de secours utilisée par un objet d'encodage quand vous instanciez l'objet.

<a name="BestFit"></a>

### <a name="best-fit-fallback"></a>Best-Fit Fallback

Quand un caractère n'a pas de correspondance exacte dans l'encodage cible, l'encodeur peut essayer de le mapper à un caractère similaire. (La stratégie de secours la mieux adaptée est principalement un codage plutôt qu'un problème de décodage. Il y a très peu de pages de code qui contiennent des caractères qui ne peuvent pas être cartographiés avec succès sur Unicode.) Le meilleur repli est la valeur par défaut pour la page de code <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> et <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> les encodages de caractères double-byte qui sont récupérés par les surcharges et.

> [!NOTE]
> En théorie, les classes d'encodage Unicode fournies dans .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding> et <xref:System.Text.UTF32Encoding>) prennent en charge tous les caractères de tous les jeux de caractères : elles peuvent donc être utilisées pour éliminer les problèmes de la stratégie de secours la mieux adaptée.

Les stratégies de secours les mieux adaptées varient pour les différentes pages de codes. Par exemple, pour certaines pages de codes, les caractères latins à pleine chasse sont mappés aux caractères latins à demi-chasse plus courants. Pour d'autres pages de codes, ce mappage n'est pas effectué. Même avec une stratégie la plus adaptée appliquée de façon agressive, il n'existe pas d'ajustement possible pour certains caractères dans certains encodages. Par exemple, un idéogramme chinois n'a pas de mappage acceptable avec la page de codes 1252. Dans ce cas, une chaîne de remplacement est utilisée. Par défaut, cette chaîne est simplement un POINT D'INTERROGATION (U+003F).

> [!NOTE]
> Les stratégies de secours les mieux adaptées ne sont pas documentées en détail. Toutefois, plusieurs pages de codes sont documentées sur le site Web du [consortium Unicode](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/). Consultez le fichier **readme.txt** de ce dossier pour obtenir une description sur la manière d’interpréter les fichiers de mappage.

L'exemple suivant utilise la page de codes 1252 (la page de codes Windows pour les langues d'Europe occidentale) pour illustrer le mappage le mieux adapté et ses inconvénients. La méthode <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> est utilisée pour récupérer un objet d'encodage pour la page de codes 1252. Par défaut, elle utilise un mappage le mieux adapté pour les caractères Unicode qu'elle ne prend pas en charge. L'exemple instancie une chaîne contenant trois caractères non-ASCII, LETTRE MAJUSCULE LATINE S CERCLÉE (U+24C8), EXPOSANT CINQ (U+2075) et INFINI (U+221E), séparés par des espaces. Comme le montre la sortie de l'exemple, quand la chaîne est encodée, les trois caractères d'origine autres qu'un espace sont remplacés par POINT D'INTERROGATION (U+003F), CHIFFRE CINQ (U+0035) et CHIFFRE HUIT (U+0038). CHIFFRE HUIT est un substitut particulièrement médiocre pour le caractère INFINI non pris en charge, et POINT D'INTERROGATION indique qu'aucun mappage n'est disponible pour le caractère d'origine.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Le mappage le mieux adapté est le comportement par défaut pour un objet <xref:System.Text.Encoding> qui encode des données Unicode en données de page de codes, et il existe des applications héritées qui s'appuient sur ce comportement. Cependant, la plupart des nouvelles applications doivent éviter ce comportement le mieux adapté pour des raisons de sécurité. Par exemple, les applications ne doivent pas établir un nom de domaine via un encodage le mieux adapté.

> [!NOTE]
> Vous pouvez également implémenter un mappage de stratégie de secours la mieux adaptée personnalisé pour un encodage. Pour plus d’informations, consultez la section [Mise en œuvre d’une stratégie de retrait personnalisée.](../../../docs/standard/base-types/character-encoding.md#Custom)

Si la stratégie de secours la mieux adaptée est la stratégie par défaut pour un objet d'encodage, vous pouvez choisir une autre stratégie de secours quand vous récupérez un objet <xref:System.Text.Encoding> , en appelant la surcharge <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> ou <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> . La section suivante contient un exemple qui remplace chaque caractère qui ne peut pas être mappé à la page de codes 1252 par un astérisque (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Replacement Fallback

Quand un caractère n'a pas de correspondance exacte dans le schéma cible, mais qu'il n'existe pas de caractère approprié auquel il peut être mappé, l'application peut spécifier un caractère ou une chaîne de remplacement. Il s'agit du comportement par défaut pour le décodeur Unicode, qui remplace toutes les séquences de deux octets qu'il ne peut pas décoder par CARACTÈRE_DE_REMPLACEMENT (U+FFFD). C'est également le comportement par défaut de la classe <xref:System.Text.ASCIIEncoding> , qui remplace chaque caractère qu'elle ne peut pas encoder ou décoder par un point d'interrogation. L'exemple suivant illustre le remplacement de caractères pour la chaîne Unicode de l'exemple précédent. Comme le montre la sortie, chaque caractère qui ne peut pas être décodé en une valeur d'octet ASCII est remplacé par 0x3F, qui est le code ASCII pour un point d'interrogation.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

.NET comprend les classes <xref:System.Text.EncoderReplacementFallback> et <xref:System.Text.DecoderReplacementFallback>, qui substituent une chaîne de remplacement si un caractère ne se mappe pas exactement dans une opération d'encodage ou de décodage. Par défaut, cette chaîne de remplacement est un point d'interrogation, mais vous pouvez appeler une surcharge de constructeur de classe pour choisir une autre chaîne. En général, la chaîne de remplacement est un caractère unique, même si ce n'est pas obligatoire. L'exemple suivant change le comportement de l'encodeur de la page de codes 1252 en instanciant un objet <xref:System.Text.EncoderReplacementFallback> qui utilise un astérisque (*) comme chaîne de remplacement.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Vous pouvez également implémenter une classe de remplacement pour un encodage. Pour plus d’informations, consultez la section [Mise en œuvre d’une stratégie de retrait personnalisée.](../../../docs/standard/base-types/character-encoding.md#Custom)

En plus du POINT D'INTERROGATION (U+003F), le CARACTÈRE DE REMPLACEMENT Unicode (U+FFFD) est couramment utilisé comme chaîne de remplacement, en particulier lors du décodage de séquences d'octets qui ne peuvent pas être converties en caractères Unicode. Vous êtes cependant libre de choisir n'importe quelle chaîne de remplacement, qui peut contenir plusieurs caractères.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Exception Fallback

Au lieu de fournir une stratégie de secours la mieux adaptée ou une chaîne de remplacement, un encodeur peut lever une <xref:System.Text.EncoderFallbackException> si elle ne peut pas encoder un jeu de caractères, et un décodeur peut lever une <xref:System.Text.DecoderFallbackException> s'il ne peut pas décoder un tableau d'octets. Pour lever une exception dans les opérations d'encodage et de décodage, vous fournissez un objet <xref:System.Text.EncoderExceptionFallback> et un objet <xref:System.Text.DecoderExceptionFallback> , respectivement, à la méthode <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> . L'exemple suivant montre la stratégie de secours pour les exceptions avec la classe <xref:System.Text.ASCIIEncoding> .

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Vous pouvez également implémenter un gestionnaire d'exceptions personnalisé pour une opération d'encodage. Pour plus d’informations, consultez la section [Mise en œuvre d’une stratégie de retrait personnalisée.](../../../docs/standard/base-types/character-encoding.md#Custom)

Les objets <xref:System.Text.EncoderFallbackException> et <xref:System.Text.DecoderFallbackException> fournissent les informations suivantes sur la condition qui a provoqué l'exception :

- L'objet <xref:System.Text.EncoderFallbackException> comprend une méthode <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> , qui indique si le ou les caractères qui ne peuvent pas être encodés représentent une paire de substitution inconnue (auquel cas la méthode retourne `true`) ou un seul caractère inconnu (auquel cas la méthode retourne `false`). Les caractères de la paire de substitution sont disponibles dans les propriétés <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> et <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> . Le caractère unique inconnu est disponible dans la propriété <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> . La propriété <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> indique la position dans la chaîne du premier caractère qui n'a pas pu être encodé.

- L'objet <xref:System.Text.DecoderFallbackException> comprend une propriété <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> qui retourne un tableau d'octets qui ne peut pas être décodé. La propriété <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> indique la position de départ des octets inconnus.

Bien que les objets <xref:System.Text.EncoderFallbackException> et <xref:System.Text.DecoderFallbackException> fournissent des informations de diagnostic adéquates sur l'exception, ils ne fournissent pas d'accès à la mémoire tampon d'encodage ou de décodage. Par conséquent, ils ne permettent pas le remplacement ou la correction des données non valides dans la méthode d'encodage ou de décodage.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Implementing a Custom Fallback Strategy

En plus du mappage le mieux adapté implémenté en interne par les pages de codes, .NET comprend les classes suivantes pour l’implémentation d’une stratégie de secours :

- Utilisez <xref:System.Text.EncoderReplacementFallback> et <xref:System.Text.EncoderReplacementFallbackBuffer> pour remplacer des caractères dans les opérations d'encodage.

- Utilisez <xref:System.Text.DecoderReplacementFallback> et <xref:System.Text.DecoderReplacementFallbackBuffer> pour remplacer des caractères dans les opérations de décodage.

- Utilisez <xref:System.Text.EncoderExceptionFallback> et <xref:System.Text.EncoderExceptionFallbackBuffer> pour lever une <xref:System.Text.EncoderFallbackException> quand un caractère ne peut pas être encodé.

- Utilisez <xref:System.Text.DecoderExceptionFallback> et <xref:System.Text.DecoderExceptionFallbackBuffer> pour lever une <xref:System.Text.DecoderFallbackException> quand un caractère ne peut pas être décodé.

En outre, vous pouvez implémenter une solution personnalisée qui utilise une stratégie de secours la mieux adaptée, une stratégie de secours pour les remplacements ou une stratégie de secours pour les exceptions, en procédant comme suit :

1. Dérivez une classe de <xref:System.Text.EncoderFallback> pour les opérations d'encodage, et de <xref:System.Text.DecoderFallback> pour les opérations de décodage.

2. Dérivez une classe de <xref:System.Text.EncoderFallbackBuffer> pour les opérations d'encodage, et de <xref:System.Text.DecoderFallbackBuffer> pour les opérations de décodage.

3. Pour la stratégie de secours pour les exceptions, si les classes prédéfinies <xref:System.Text.EncoderFallbackException> et <xref:System.Text.DecoderFallbackException> ne répondent pas à vos besoins, dérivez une classe depuis un objet d'exception comme <xref:System.Exception> ou <xref:System.ArgumentException>.

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Dérivation depuis EncoderFallback ou DecoderFallback

Pour implémenter une solution de stratégie de secours personnalisée, vous devez créer une classe qui hérite de <xref:System.Text.EncoderFallback> pour les opérations d'encodage, et de <xref:System.Text.DecoderFallback> pour les opérations de décodage. Les instances de ces classes sont passées à la méthode <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> et elle servent d'intermédiaire entre la classe d'encodage et l'implémentation de la stratégie de secours.

Quand vous créez une solution de secours personnalisée pour un encodeur ou un décodeur, vous devez implémenter les membres suivants :

- La propriété <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> , qui retourne le nombre maximal possible de caractères qui peuvent être retournés par la stratégie de secours la mieux adaptée, par la stratégie de secours pour les remplacements ou par la stratégie de secours pour les exceptions pour remplacer un caractère unique. Pour une stratégie de secours pour les exceptions personnalisée, sa valeur est zéro.

- La méthode <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> , qui retourne votre implémentation personnalisée de <xref:System.Text.EncoderFallbackBuffer> ou de <xref:System.Text.DecoderFallbackBuffer> . La méthode est appelée par l'encodeur quand il rencontre le premier caractère qu'il est impossible d'encoder correctement, ou par le décodeur quand il rencontre le premier octet qu'il est impossible de décoder correctement.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Dérivation depuis EncoderFallbackBuffer ou DecoderFallbackBuffer

Pour implémenter une solution de secours personnalisée, vous devez aussi créer une classe qui hérite de <xref:System.Text.EncoderFallbackBuffer> pour les opérations d'encodage, et de <xref:System.Text.DecoderFallbackBuffer> pour les opérations de décodage. Les instances de ces classes sont retournées par la méthode <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> des classes <xref:System.Text.EncoderFallback> et <xref:System.Text.DecoderFallback> . La méthode <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> est appelée par l'encodeur quand il rencontre le premier caractère qu'il ne peut pas encoder, et la méthode <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> est appelée par le décodeur quand il rencontre un ou plusieurs octets qu'il ne peut pas décoder. Les classes <xref:System.Text.EncoderFallbackBuffer> et <xref:System.Text.DecoderFallbackBuffer> fournissent l'implémentation de la stratégie de secours. Chaque instance représente une mémoire tampon qui contient les caractères de secours destinés à remplacer le caractère qui ne peut pas être encodé ou la séquence d'octets qui ne peut pas être décodée.

Quand vous créez une solution de secours personnalisée pour un encodeur ou un décodeur, vous devez implémenter les membres suivants :

- La méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> . <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> est appelée par l'encodeur pour fournir à la mémoire tampon de secours des informations concernant le caractère qu'elle ne peut pas encoder. Étant donné que le caractère à encoder peut être une paire de substitution, cette méthode est surchargée. Le caractère à encoder et son index dans la chaîne sont passés à une surcharge. La demi-zone haute et la demi-zone basse, ainsi que son index dans la chaîne, sont passés à la deuxième surcharge. La méthode <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> est appelée par le décodeur pour fournir à la mémoire tampon de secours des informations sur les octets qu'elle ne peut pas décoder. Cette méthode reçoit un tableau d'octets qu'elle ne peut pas décoder, ainsi que l'index du premier octet. La méthode de secours doit retourner `true` si la mémoire tampon de secours peut fournir un ou plusieurs caractères les mieux adaptés ou de remplacement ; sinon, elle doit retourner `false`. Pour une stratégie de secours pour les exceptions, la méthode de secours doit lever une exception.

- La méthode <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> , qui est appelée de façon répétée par l'encodeur ou par le décodeur pour obtenir le caractère suivant de la mémoire tampon de secours. Quand tous les caractères de secours ont été retournés, la méthode doit retourner U+0000.

- La propriété <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> , qui retourne le nombre de caractères restants dans la mémoire tampon de secours.

- La méthode <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> , qui déplace la position actuelle dans la mémoire tampon de secours au caractère précédent.

- La méthode <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> , qui réinitialise la mémoire tampon de secours.

Si l'implémentation de la stratégie de secours est une stratégie de secours la mieux adaptée ou de remplacement, les classes dérivées de <xref:System.Text.EncoderFallbackBuffer> et de <xref:System.Text.DecoderFallbackBuffer> gèrent également deux champs d'instance privés : le nombre exact de caractères dans la mémoire tampon et l'index du caractère suivant dans la mémoire tampon à retourner.

### <a name="an-encoderfallback-example"></a>Exemple de stratégie de secours d'encodeur

L'exemple précédent utilisait une stratégie de sauvegarde pour les remplacements pour remplacer les caractères Unicode qui ne correspondaient pas aux caractères ASCII par un astérisque (*). L'exemple suivant utilise à la place une implémentation de stratégie de secours la mieux adaptée personnalisée pour fournir un meilleur mappage des caractères non-ASCII.

Le code suivant définit une classe nommée `CustomMapper` qui est dérivée de <xref:System.Text.EncoderFallback> pour gérer le mappage le mieux adapté des caractères non-ASCII. Sa méthode `CreateFallbackBuffer` retourne un objet `CustomMapperFallbackBuffer` , qui fournit l'implémentation de <xref:System.Text.EncoderFallbackBuffer> . La classe `CustomMapper` utilise un objet <xref:System.Collections.Generic.Dictionary%602> pour stocker les mappages des caractères Unicode non pris en charge (la valeur de la clé) et leurs caractères 8 bits correspondants (qui sont stockés dans deux octets consécutifs dans un entier 64 bits). Pour que ce mappage soit disponible pour la mémoire tampon de secours, l'instance de `CustomMapper` est passée comme paramètre au constructeur de classe `CustomMapperFallbackBuffer` . Comme le mappage le plus long est la chaîne "INF" pour le caractère Unicode U+221E, la propriété `MaxCharCount` retourne 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Le code suivant définit la classe `CustomMapperFallbackBuffer` , qui est dérivée de <xref:System.Text.EncoderFallbackBuffer>. Le dictionnaire qui contient les mappages les mieux adaptés et qui est défini dans l'instance de `CustomMapper` est disponible à partir de son constructeur de classe. Sa méthode `Fallback` retourne `true` si un des caractères Unicode que l'encodeur ASCII ne peut pas encoder est défini dans le dictionnaire de mappage ; sinon, elle retourne `false`. Pour chaque stratégie de secours, la variable privée `count` indique le nombre de caractères qui restent à retourner, et la variable privée `index` indique la position du caractère suivant à retourner dans la mémoire tampon de la chaîne, `charsToReturn`.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Le code suivant instancie ensuite l'objet `CustomMapper` et passe une instance de celui-ci à la méthode <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> . La sortie indique que l'implémentation de la stratégie de secours la mieux adaptée gère correctement les trois caractères non-ASCII de la chaîne d'origine.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalisation et localisation](../../../docs/standard/globalization-localization/index.md)
