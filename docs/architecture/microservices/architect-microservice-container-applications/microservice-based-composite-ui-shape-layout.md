---
title: Création d’une interface utilisateur composite basée sur des microservices
description: Une architecture de microservices n’est pas uniquement conçue pour le back-end. Elle peut également s’utiliser dans un environnement front-end comme vous allez pouvoir le voir.
ms.date: 09/20/2018
ms.openlocfilehash: 60e0e6d59738f3f1fec31226cb842ceb1af303e4
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834377"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Création d’une interface utilisateur composite basée sur des microservices

L’architecture de microservices commence généralement par la gestion côté serveur des données et de la logique. Cependant, une approche plus avancée consiste à concevoir l’interface utilisateur de votre application également en fonction de microservices. Ceci implique d’avoir une interface utilisateur composite produite par les microservices, et non pas des microservices sur le serveur et simplement une application cliente monolithique consommant les microservices. Avec cette approche, les microservices que vous créez peuvent être complets, avec à la fois la logique et une représentation visuelle.

La figure 4-20 montre une approche plus simple consistant à seulement consommer des microservices à partir d’une application cliente monolithique. Bien sûr, vous pourriez avoir un service ASP.NET MVC intermédiaire produisant du code HTML et JavaScript. La figure est une simplification qui met en évidence le fait que vous avez une interface utilisateur cliente (monolithique) consommant les microservices, qui s’occupe seulement de la logique et des données, mais pas de la forme de l’interface utilisateur (HTML et JavaScript).

![Diagramme d’une application d’interface utilisateur monolithique se connectant aux microservices.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Figure 4-20**. Une application avec interface utilisateur monolithique consommant des microservices de backend

En revanche, une interface utilisateur composite est précisément générée et composée par les microservices eux-mêmes. Certains des microservices déterminent la forme visuelle de zones spécifiques de l’interface utilisateur. La principale différence est que vous avez des composants d’interface utilisateur clients (par exemple, des classes TypeScript) basés sur des modèles, et que le ViewModel de l’interface utilisateur qui met en forme les données pour ces modèles est fourni par chaque microservice.

Au démarrage de l’application cliente, chacun des composants de l’interface utilisateur cliente (par exemple des classes TypeScript) s’inscrit lui-même auprès d’un microservice de l’infrastructure capable de fournir des ViewModel pour un scénario donné. Si le microservice change la forme, l’interface utilisateur change également.

La figure 4-21 montre une version de cette approche de l’interface utilisateur composite. C’est une version simplifiée, car vous pouvez avoir d’autres microservices qui agrègent des parties plus petites selon différentes techniques. Cela dépend de ce que vous créez : une application web traditionnelle (ASP.NET MVC) ou une application monopage (SPA).

![Diagramme d’une interface utilisateur composite constituée de nombreux modèles de vue.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Figure 4-21**. Exemple d’une application d’interface utilisateur composite mise en forme des microservices de backend

Chacun de ces microservices de composition de l’interface utilisateur serait similaire à une petite passerelle d’API. Mais dans ce cas, chacun d’entre eux est responsable d’une petite zone d’interface utilisateur.

Une approche d’interface utilisateur composite basée sur des microservices peut être plus ou moins difficile à implémenter, selon les technologies d’interface utilisateur que vous utilisez. Par exemple, vous n’utilisez pas les mêmes techniques pour créer une application web traditionnelle que pour créer une application monopage ou pour des applications mobiles natives (comme quand vous développez des applications Xamarin, ce qui peut s’avérer plus difficile avec cette approche).

L’exemple d’application [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) utilise l’approche de l’interface utilisateur monolithique pour plusieurs raisons. D’abord, elle constitue une introduction aux microservices et aux conteneurs. Une interface utilisateur composite est plus avancée, mais engendre plus de complexité dans la conception et le développement de l’interface utilisateur. En second lieu, eShopOnContainers fournit également une application mobile native basée sur Xamarin, ce qui rendrait plus complexe le code C\# côté client.

Nous vous encourageons cependant à utiliser les références suivantes pour en savoir plus sur les interfaces utilisateur composites basées sur des microservices.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Composite UI using ASP.NET (atelier Particular)**  \
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. The Monolithic Frontend in the Microservices Architecture** \
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. The secret of better UI composition** \
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic. Including Front-End Web Components Into Microservices** \
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Managing Frontend in the Microservices Architecture** \
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Précédent](microservices-addressability-service-registry.md)
>[Suivant](resilient-high-availability-microservices.md)
