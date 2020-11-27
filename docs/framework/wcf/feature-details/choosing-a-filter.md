---
title: Choix d'un filtre
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: f783b6416f2330d272c4c756a3ca0cd332f3c6e7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276098"
---
# <a name="choosing-a-filter"></a>Choix d'un filtre

Lors de la configuration du service de routage, il est important de sélectionner des filtres de message corrects et de les configurer pour vous permettre d'établir des correspondances exactes avec les messages que vous recevez. Si les filtres que vous sélectionnez établissent des correspondances trop générales ou ne sont pas configurés correctement, les messages sont routés de manière incorrecte. Si les filtres sont trop restrictifs, vous risquez de ne pas disposer d'itinéraires valides disponibles pour certains de vos messages.

## <a name="filter-types"></a>Types de filtres.

Lors de la sélection des filtres utilisés par le service de routage, il est important de connaître le fonctionnement de chaque filtre, ainsi que les informations disponibles dans le cadre des messages entrants. Par exemple, si tous les messages sont reçus sur le même point de terminaison, les filtres Adresse et EndpointName sont inutiles, parce que tous les messages correspondent à ces filtres.

### <a name="action"></a>Action

Le filtre Action inspecte la propriété <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A>. Si le contenu de l'en-tête Action du message correspond à la valeur des données de filtre spécifiée dans la configuration du filtre, alors ce filtre retourne `true`. L’exemple suivant définit un `FilterElement` qui utilise le filtre d’action pour faire correspondre les messages avec un en-tête d’action qui contient une valeur de `http://namespace/contract/operation/` .

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

Ce filtre doit être utilisé lors du routage des messages qui contiennent un en-tête Action unique.

### <a name="endpointaddress"></a>EndpointAddress

Le filtre EndpointAddress inspecte l'EndpointAddress sur lequel le message a été reçu. Si l'adresse à laquelle le message arrive correspond exactement à l'adresse de filtre spécifiée dans la configuration de filtre, ce filtre retourne `true`. L’exemple suivant définit un `FilterElement` qui utilise le filtre d’adresse pour faire correspondre tous les messages adressés à « http:// \<hostname> /vdir/s.svc/b ».

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> Il est important de noter que la partie nom d'hôte d'une adresse peut différer selon que le client utilise le nom de domaine complet, le nom NetBIOS, l'adresse IP ou un autre nom. Étant donné que des valeurs différentes peuvent faire référence au même hôte, le comportement par défaut de cette comparaison consiste à ne pas utiliser la partie nom d'hôte de l'adresse pour effectuer des correspondances.
>
> Ce comportement peut être modifié pour permettre à la comparaison d'évaluer le nom d'hôte lors de la configuration du service de routage par programme.

Ce filtre doit être utilisé lorsque les messages entrants sont adressés à une adresse unique.

### <a name="endpointaddressprefix"></a>EndpointAddressPrefix

Le filtre EndpointAddressPrefix est semblable au filtre EndpointAddress. Le filtre EndpointAddressPrefix inspecte l'EndpointAddress sur lequel le message a été reçu. Toutefois, le filtre EndpointAddressPrefix agit comme un caractère générique en correspondant aux adresses qui commencent par la valeur spécifié dans la configuration de filtre. L’exemple suivant définit un `FilterElement` qui utilise le filtre EndpointAddressPrefix pour faire correspondre tous les messages adressés à `http://<hostname>/vdir*` .

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> Il est important de noter que la partie nom d'hôte d'une adresse peut différer selon que le client utilise le nom de domaine complet, le nom NetBIOS, l'adresse IP ou un autre nom. Étant donné que des valeurs différentes peuvent faire référence au même hôte, le comportement par défaut de cette comparaison consiste à ne pas utiliser la partie nom d'hôte de l'adresse pour effectuer des correspondances.

Ce filtre doit être utilisé lors du routage des messages entrants qui partagent un préfixe d'adresse commun.

### <a name="and"></a>AND

Le filtre AND ne filtre pas directement sur une valeur dans un message, mais vous permet de combiner deux autres filtres pour créer une condition `AND` où les deux filtres doivent correspondre au message pour que le filtre AND retourne la valeur `true`. Cela vous permet de créer des filtres complexes qui établissent une correspondance uniquement si tous les sous-filtres correspondent. L'exemple suivant définit un filtre d'adresse et un filtre d'action, puis définit un filtre AND qui évalue un message en fonction de ces deux filtres d'action et d'adresse. Si les filtres d'adresse et d'action correspondent tous les deux, alors le filtre AND retourne `true`.

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

Ce filtre doit être utilisé lorsque vous devez combiner la logique de plusieurs filtres pour déterminer quand une correspondance doit être établie. Par exemple, si vous avez plusieurs destinations qui doivent recevoir uniquement certaines combinaisons d'actions et de messages à des adresses particulières, vous pouvez utiliser un filtre AND pour combiner les filtres Action et Adresse nécessaires.

### <a name="custom"></a>Custom

Lorsque vous sélectionnez le type de filtre personnalisé, vous devez fournir une valeur customType qui contient le type de l’assembly qui contient l’implémentation **MessageFilter** à utiliser pour ce filtre. En outre, le filterData doit contenir les valeurs requises par le filtre personnalisé pour son évaluation des messages. L'exemple suivant définit un `FilterElement` qui utilise l'implémentation de MessageFilter `CustomAssembly.MyCustomMsgFilter`.

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

Si vous devez exécuter une logique de correspondance personnalisée sur un message qui n’est pas couvert par les filtres fournis avec [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] , vous devez créer un filtre personnalisé qui est une implémentation de la classe **MessageFilter** . Par exemple, vous pouvez créer un filtre personnalisé qui compare un champ dans le message entrant à une liste de valeurs connues données au filtre en tant que configuration, ou qui hache un élément de message particulier, puis examine cette valeur pour déterminer si le filtre doit retourner `true` ou `false`.

### <a name="endpointname"></a>EndpointName

Le filtre EndpointName inspecte le nom du point de terminaison qui a reçu le message. L’exemple suivant définit un `FilterElement` qui utilise le filtre EndpointName pour acheminer les messages reçus sur « SvcEndpoint ».

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

Ce filtre est utile lorsque le service de routage expose plusieurs points de terminaison de service nommés. Par exemple, vous pouvez exposer deux points de terminaison que le service de routage utilise pour recevoir des messages ; l'un est utilisé par les clients prioritaires qui nécessitent un traitement en temps réel de leurs messages, tandis que l'autre reçoit des messages pour lesquels le délai importe peu.

Une correspondance de l'adresse complète est souvent utilisée pour déterminer sur quel point de terminaison un message a été reçu. Cependant, utiliser le nom défini du point de terminaison est un raccourci commode souvent moins sujet aux erreurs, notamment dans le cas d'une configuration de service de routage à l'aide d'un fichier de configuration (où les noms des points de terminaison sont un attribut obligatoire).

### <a name="matchall"></a>MatchAll

Le filtre MatchAll correspond à n'importe quel message reçu. Il est utile si vous devez toujours router l'ensemble des messages reçus vers un point de terminaison spécifique, tel qu'un service de journalisation qui stocke une copie de tous les messages reçus. L'exemple suivant définit un `FilterElement` qui utilise le filtre MatchAll.

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a>XPath

Le filtre XPath vous permet de spécifier une requête XPath utilisée pour inspecter un élément spécifique dans le message. Le filtrage XPath est une option de filtrage puissante qui vous permet d’inspecter directement toute entrée XML adressable dans le message ; toutefois il requiert une connaissance spécifique de la structure des messages que vous recevez. L’exemple suivant définit un `FilterElement` qui utilise le filtre XPath pour inspecter le message d’un élément nommé « element » dans l’espace de noms référencé par le préfixe d’espace de noms « ns ».

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

Ce filtre est utile si vous savez que les messages que vous recevez contiennent une valeur spécifique. Par exemple, vous hébergez deux versions du même service et savez que les messages adressés à la version la plus récente du service contiennent une valeur unique dans un en-tête personnalisé. Vous pouvez créer un filtre qui utilise XPath pour accéder à cet en-tête. Le filtre compare la valeur présente dans l'en-tête à une autre indiquée dans la configuration du filtre, afin de déterminer si le filtre correspond.

Étant donné que les requêtes XPath contiennent souvent des espaces de noms uniques, qui sont souvent des valeurs de chaîne longues ou complexes, le filtre XPath vous permet d’utiliser la table d’espace de noms pour définir des préfixes uniques pour vos espaces de noms. Pour plus d’informations sur la table d’espace de noms, consultez [filtres de messages](message-filters.md).

Pour plus d’informations sur la conception de requêtes XPath, consultez [syntaxe XPath](/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).

## <a name="see-also"></a>Voir aussi

- [Filtres de message](message-filters.md)
- [Procédure : utiliser des filtres](how-to-use-filters.md)
