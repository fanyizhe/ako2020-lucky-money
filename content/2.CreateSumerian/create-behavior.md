
---
title: "Add Action Behaviors"
chapter: false
weight: 22
---


## Add Assets Action Behaviors 

####  Red Packet 

1. On the left side **Entities** panel, delete **Default Camera**.
    ![](/images/addSumerian/add-behaviors-delete-default-camera.png)

1.  Select the **LuckyMoney** entity
    ![](/images/addSumerian/add-behaviors-select-packet.png)

1. Click **Add Component**, choose **State Machine**.    
   ![](/images/addSumerian/add-component.png)   
   
   ![](/image/WechatIMG8.png)   sel

1. Click the **+ button**  to add behavior.     
   ![](/image/WechatIMG11.png)

1. Name the **behavior name** and the **state name** `wait for click`

1. Click **Add Action**    
   ![](/image/WechatIMG13.png)

1. Find **Click/Tap on entity** in the list or search it in the search bar. Don't forget to **Add** it.   
   ![](/image/WechatIMG14.png)

1. Click **Add State** and change the **state name** to `hide`   
   ![](/image/WechatIMG15.png)
   
1. Click **Add Action**. Find and add **Hide**   
   ![](/image/WechatIMG19.png)

1. Add another action. Click **Add Action** and add **Emit Message**   
   ![](/image/WechatIMG21.png)

1. In the **channel**, enter `showMoney`      
   ![](/image/WechatIMG23.png)

1. Add another action **Execute Script**. Click the **+** button to add script, choose **Custom (Legacy Format)**. 
    ![](/image/script-create-script.png)

    ![](/image/script-choose-type.png)

1. Click the **pencil** button to edit script, copy the following codes into the function **enter**, then save the change.
    ![](/image/script-edit-script.png)
    
    {{< highlight javascript >}}
        window.postMessage('sumerian-open-packet','*');
        ctx.transitions.success();
    {{< /highlight >}}

    ![](/image/script-save-change.png)

1. Click the **wait for click** state, drag a line from **On Click/Tap Entity** to **hide** state.
   ![](/images/addSumerian/script-drag-line.png)

#### Red Packet with Money 

1. Click the **LuckyMoneyWithCash** entity.   

1. Click **Add Component** button, choose **State Machine**    

1. Click the **+ button**     

1. Name both the **behavior name** and the **state name** to `listen`    

1. Click **Add Action**    

1. Find **Listen** and click **Add**    
   ![](/image/WechatIMG24.png)

1. In the **Message Channel** under **Selected State**, enter `showMoney`
    
1. Click **+ Add State** and name it `show`

1. Click **Add action** and add **Show**    

1. Drag a line from **On 'showMoney' event** under **listen** state to **show** state   
    ![](/images/addSumerian/script-drag-line-2.png)

#### Share Button

1. Click the **Share Btn** entity, click **Add Component**, and select **State Machine**.

1. Create a behavior, name both the **behavior name** and the **state name** `ListenForClickShare`.
    ![](/image/share-button-behaviors.png)

1. Click **Add Action**, select **Click/Tap on entity**.

1. Create another state by click **+ Add State**, name it `ExeShareScript`.

1. Add another action **Execute Script**. Click the **+ button** to add script, choose **Custom (Legacy Format)**. 

1. Click the **pencil** button to edit script, copy the following codes into the function **enter**, then **save** the change.

    {{< highlight javascript >}}
	    window.postMessage('sumerian-share-packet','*');
	    ctx.transitions.success();
    {{< /highlight >}}

    ![](/image/share-button-save-script.png)

1. Drag a line from **On Click/Tap Entity** action under **ListenForClickShare** state to **ExeShareScipt** state
    ![](/images/addSumerian/script-drag-line-3.png)


#### Close Button

The steps are similar to **Share Button**. So repeat the steps **Share Button**, change all the names from **shate** to **close**, and use the following codes instead of the previous one in **edit script**.

{{< highlight javascript >}}
    window.postMessage('sumerian-close-packet','*');
    ctx.transitions.success();
{{< /highlight >}}

![](/images/addSumerian/script-drag-line-4.png)

## Config Default Hidden
1. Click the eye button on the left console, the corresponding entity will be disappear.
   ![](/images/addSumerian/hide-cash.png)


## Set AR Camera

1. Find the main AR Camera using the left navigation bar

1. Change the **Z** value of position to `2` and save the scene

![](/images/addSumerian/change-camera.png)

## Conclusion
Congratulations! You have completed the sumerian settings. So far, we cannot test the final effects as it has not been integrated with our application yet. In the next session, we will create a React web application.

