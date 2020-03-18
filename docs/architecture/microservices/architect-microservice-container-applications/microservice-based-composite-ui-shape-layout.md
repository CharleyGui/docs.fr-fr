---
title: Création d’une interface utilisateur composite basée sur des microservices
description: Une architecture de microservices n’est pas uniquement conçue pour le back-end. Elle peut également s’utiliser dans un environnement front-end comme vous allez pouvoir le voir.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72275739"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Création d’une interface utilisateur composite basée sur des microservices

L’architecture des microservices commence souvent par les données de manipulation du côté du serveur et la logique, mais, dans de nombreux cas, l’interface utilisateur est toujours traitée comme un monolithe. Cependant, une approche plus avancée, appelée [micro frontends](https://martinfowler.com/articles/micro-frontends.html), est de concevoir votre interface utilisateur d’application basée sur les microservices ainsi. Ceci implique d’avoir une interface utilisateur composite produite par les microservices, et non pas des microservices sur le serveur et simplement une application cliente monolithique consommant les microservices. Avec cette approche, les microservices que vous créez peuvent être complets, avec à la fois la logique et une représentation visuelle.

La figure 4-20 montre une approche plus simple consistant à seulement consommer des microservices à partir d’une application cliente monolithique. Bien sûr, vous pourriez avoir un service ASP.NET MVC intermédiaire produisant du code HTML et JavaScript. La figure est une simplification qui met en évidence le fait que vous avez une interface utilisateur cliente (monolithique) consommant les microservices, qui s’occupe seulement de la logique et des données, mais pas de la forme de l’interface utilisateur (HTML et JavaScript).

![Diagramme d’une application d’interface utilisateur monolithique se connectant aux microservices.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Figure 4-20**. Une application avec interface utilisateur monolithique consommant des microservices de backend

En revanche, une interface utilisateur composite est précisément générée et composée par les microservices eux-mêmes. Certains des microservices déterminent la forme visuelle de zones spécifiques de l’interface utilisateur. La principale différence est que vous avez des composants d’interface utilisateur clients (par exemple, des classes TypeScript) basés sur des modèles, et que le ViewModel de l’interface utilisateur qui met en forme les données pour ces modèles est fourni par chaque microservice.

Au démarrage de l’application cliente, chacun des composants de l’interface utilisateur cliente (par exemple des classes TypeScript) s’inscrit lui-même auprès d’un microservice de l’infrastructure capable de fournir des ViewModel pour un scénario donné. Si le microservice change la forme, l’interface utilisateur change également.

La figure 4-21 montre une version de cette approche de l’interface utilisateur composite. C’est une version simplifiée, car vous pouvez avoir d’autres microservices qui agrègent des parties plus petites selon différentes techniques. Cela dépend de ce que vous créez : une application web traditionnelle (ASP.NET MVC) ou une application monopage (SPA).

![Diagramme d’une interface utilisateur composite composée de nombreux modèles de vue.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Figure 4-21**. Exemple d’une application d’interface utilisateur composite mise en forme des microservices de backend

Chacun de ces microservices de composition de l’interface utilisateur serait similaire à une petite passerelle d’API. Mais dans ce cas, chacun est responsable d’une petite zone d’assurance-chômage.

Une approche d’interface utilisateur composite basée sur des microservices peut être plus ou moins difficile à implémenter, selon les technologies d’interface utilisateur que vous utilisez. Par exemple, vous n’utilisez pas les mêmes techniques pour créer une application web traditionnelle que pour créer une application monopage ou pour des applications mobiles natives (comme quand vous développez des applications Xamarin, ce qui peut s’avérer plus difficile avec cette approche).

L’exemple d’application [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) utilise l’approche de l’interface utilisateur monolithique pour plusieurs raisons. D’abord, elle constitue une introduction aux microservices et aux conteneurs. Une interface utilisateur composite est plus avancée, mais engendre plus de complexité dans la conception et le développement de l’interface utilisateur. En second lieu, eShopOnContainers fournit également une application mobile native basée sur Xamarin, ce qui rendrait plus complexe le code C\# côté client.

Nous vous encourageons cependant à utiliser les références suivantes pour en savoir plus sur les interfaces utilisateur composites basées sur des microservices.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Micro Frontends (blog de Martin Fowler)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **Micro Frontends (site Michael Geers)**  
  <https://micro-frontends.org/>
  
- **Composite UI using ASP.NET (atelier Particular)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. Le Frontend monolithique dans l’architecture microservices**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. Le secret d’une meilleure composition de l’interface utilisateur**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic. Inclure les composants Web front-end dans les microservices**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Managing Frontend in the Microservices Architecture**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Suivant précédent](microservices-addressability-service-registry.md)
>[Next](resilient-high-availability-microservices.md)
