---
title: 'Comment : sécuriser des messages au sein de sessions fiables'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141666"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="f45c7-102">Comment : sécuriser des messages au sein de sessions fiables</span><span class="sxs-lookup"><span data-stu-id="f45c7-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="f45c7-103">Cette rubrique décrit les étapes requises pour activer la sécurité au niveau du message pour les messages échangés dans une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut.</span><span class="sxs-lookup"><span data-stu-id="f45c7-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="f45c7-104">Activez une session sécurisée et fiable soit de manière impérative en utilisant le code, soit de façon déclarative dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f45c7-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="f45c7-105">Cette procédure utilise le client et les fichiers de configuration du service pour activer la session fiable sécurisée.</span><span class="sxs-lookup"><span data-stu-id="f45c7-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="f45c7-106">La procédure inclut les trois tâches clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f45c7-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="f45c7-107">Spécifiez que le client et le service échangent des messages dans une session fiable.</span><span class="sxs-lookup"><span data-stu-id="f45c7-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="f45c7-108">Requérez la sécurité au niveau du message dans la session fiable.</span><span class="sxs-lookup"><span data-stu-id="f45c7-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="f45c7-109">Spécifiez le type d'informations d'identification que le client doit utiliser pour être authentifié auprès du service.</span><span class="sxs-lookup"><span data-stu-id="f45c7-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="f45c7-110">Il est important, dans la première tâche, que l’élément de configuration de point de terminaison contienne un attribut `bindingConfiguration` qui référence une configuration de liaison nommée (dans cet exemple) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="f45c7-111">La [**liaison\<** ](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration référence ensuite ce nom pour activer des sessions fiables en affectant à l’attribut `enabled` de l’élément [ **\<ReliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="f45c7-112">Vous pouvez requérir que les assurances de remise ordonnée soient disponibles dans une session fiable en affectant à l'attribut `ordered` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="f45c7-113">Pour obtenir la copie source de l’exemple sur lequel cette procédure de configuration est basée, consultez la [session WS Reliable](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="f45c7-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="f45c7-114">Les éléments essentiels de la deuxième tâche sont obtenus en définissant l’attribut `mode` de l’élément de **> de sécurité\<** contenu dans l’élément **> de liaison\<** du client et du service à `Message`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="f45c7-115">Les éléments essentiels de la troisième tâche sont obtenus en définissant l’attribut `clientCredentialType` de l’élément **\<message** contenu dans l’élément **\<Security >** du client et du service sur `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="f45c7-116">Lors de l’utilisation de la sécurité de message avec des sessions fiables, la messagerie fiable tente d’authentifier un client non authentifié jusqu’à ce qu’un délai d’attente se produise au lieu de lever une exception lors du premier échec.</span><span class="sxs-lookup"><span data-stu-id="f45c7-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f45c7-117">Configurer le service avec une liaison WSHttpBinding pour utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="f45c7-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="f45c7-118">Cette procédure est décrite dans [Comment : échanger des messages au sein d’une session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="f45c7-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f45c7-119">Configurer le client avec une liaison WSHttpBinding pour utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="f45c7-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="f45c7-120">Cette procédure est décrite dans [Comment : échanger des messages au sein d’une session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="f45c7-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="f45c7-121">Définir le mode et ClientCredentialType dans la configuration</span><span class="sxs-lookup"><span data-stu-id="f45c7-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="f45c7-122">Ajoutez un élément de liaison approprié aux [**liaisons\<** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f45c7-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="f45c7-123">L’exemple suivant ajoute un élément [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f45c7-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="f45c7-124">Ajoutez un élément de **> de liaison\<** et affectez à son attribut `name` une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="f45c7-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="f45c7-125">L’exemple utilise le nom `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="f45c7-126">Ajoutez un élément **\<security >** et affectez à l’attribut `mode` la valeur `Message`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="f45c7-127">Dans l’élément **\<security >** , ajoutez un élément **\<message >** et affectez à l’attribut `clientCredentialType` la valeur `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="f45c7-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
