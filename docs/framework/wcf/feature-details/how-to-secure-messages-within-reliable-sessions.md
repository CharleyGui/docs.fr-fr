---
title: 'Procédure : sécuriser des messages au sein de sessions fiables'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: cec9356467886be022d05ead55d5cb6ccddcd838
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558678"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="3b9d0-102">Procédure : sécuriser des messages au sein de sessions fiables</span><span class="sxs-lookup"><span data-stu-id="3b9d0-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="3b9d0-103">Cette rubrique décrit les étapes requises pour activer la sécurité au niveau du message pour les messages échangés dans une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="3b9d0-104">Activez une session sécurisée et fiable soit de manière impérative en utilisant le code, soit de façon déclarative dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="3b9d0-105">Cette procédure utilise le client et les fichiers de configuration du service pour activer la session fiable sécurisée.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="3b9d0-106">La procédure inclut les trois tâches clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3b9d0-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="3b9d0-107">Spécifiez que le client et le service échangent des messages dans une session fiable.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="3b9d0-108">Requérez la sécurité au niveau du message dans la session fiable.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="3b9d0-109">Spécifiez le type d'informations d'identification que le client doit utiliser pour être authentifié auprès du service.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="3b9d0-110">Il est important, dans la première tâche, que l’élément de configuration de point de terminaison contienne un `bindingConfiguration` attribut qui référence une configuration de liaison nommée (dans cet exemple) `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="3b9d0-111">L' [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration référence ensuite ce nom pour activer des sessions fiables en affectant `enabled` à l’attribut de l’élément la valeur [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) `true` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="3b9d0-112">Vous pouvez requérir que les assurances de remise ordonnée soient disponibles dans une session fiable en affectant à l'attribut `ordered` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="3b9d0-113">Pour obtenir la copie source de l’exemple sur lequel cette procédure de configuration est basée, consultez la [session WS Reliable](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="3b9d0-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="3b9d0-114">Les éléments essentiels de la deuxième tâche sont atteints en affectant `mode` à l’attribut de l' **\<security>** élément contenu dans l' **\<binding>** élément du client et du service la valeur `Message` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="3b9d0-115">Les éléments essentiels de la troisième tâche sont atteints en affectant `clientCredentialType` à l’attribut de l' **\<message>** élément contenu dans l' **\<security>** élément du client et du service la valeur `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="3b9d0-116">Lors de l’utilisation de la sécurité de message avec des sessions fiables, la messagerie fiable tente d’authentifier un client non authentifié jusqu’à ce qu’un délai d’attente se produise au lieu de lever une exception lors du premier échec.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="3b9d0-117">Configurer le service avec une liaison WSHttpBinding pour utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="3b9d0-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="3b9d0-118">Cette procédure est décrite dans [Comment : échanger des messages au sein d’une session fiable](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="3b9d0-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="3b9d0-119">Configurer le client avec une liaison WSHttpBinding pour utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="3b9d0-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="3b9d0-120">Cette procédure est décrite dans [Comment : échanger des messages au sein d’une session fiable](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="3b9d0-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="3b9d0-121">Définir le mode et ClientCredentialType dans la configuration</span><span class="sxs-lookup"><span data-stu-id="3b9d0-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="3b9d0-122">Ajoutez un élément de liaison approprié à l' [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="3b9d0-123">L’exemple suivant ajoute un [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="3b9d0-124">Ajoutez un **\<binding>** élément et affectez `name` à son attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="3b9d0-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="3b9d0-125">L’exemple utilise le nom `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="3b9d0-126">Ajoutez un **\<security>** élément et affectez `mode` à l’attribut la valeur `Message` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="3b9d0-127">Dans l' **\<security>** élément, ajoutez un **\<message>** élément et affectez `clientCredentialType` à l’attribut la valeur `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="3b9d0-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
