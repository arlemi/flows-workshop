# flows-workshop

## Quick start

This quick start tutorial creates a flow to check if a website is down or not. It does this by sending a request to the website and looking for a `200` status code in the response. If the website is up and running, the flow's **Output** block will display `True`. If the website is down, it will display `False`.

1. Go to the [**DevOps Flows**](https://www.postman.com/postman/workspace/devops-flows) workspace and [fork](/docs/collaborating-in-postman/using-version-control/forking-entities/) the [**DownDetector**](https://www.postman.com/postman/workspace/devops-flows/collection/23919558-2ea958e4-8647-4b79-859a-47a2c7608b4d?action=share&creator=23919558) collection to your workspace. Then, in your workspace, select **New &gt; Flows** and [hide the sidebar](/docs/getting-started/navigating-postman/#sidebar).

    ![Fork the collection](https://assets.postman.com/postman-docs/v10/flow-tut-fork-collection-1-v10.gif)

1. Right-click the canvas and select **Send Request** from the list of blocks. Connect the **Send Request** block to the **Start** block.

    ![Create a **Send Request** block and connect it](https://assets.postman.com/postman-docs/v10/flow-tut-add-send-v10.gif)

1. In the **Send Request** block, select **Add request &gt; DownDetector &gt; sitemap**. Then select the port next to **Success**, and drag and drop it to the right. Select **Evaluate** from the list that appears to add an **Evaluate** block.

    ![Add an **Evaluate** block](https://assets.postman.com/postman-docs/v10/flow-tut-add-eval-v10.gif)

1. In the **Evaluate** block, select `value1` and change it to `status`. Then select **Enter path...**, scroll down, and select **http.status**.

    ![Rename value1 and select `http.status`](https://assets.postman.com/postman-docs/v10/flow-tut-select-status-v10.gif)

1. Select **Start writing an FQL query...** and enter `status=200`.

    ![Enter `status=200`](https://assets.postman.com/postman-docs/v10/flow-tut-status-200-v10.gif)

1. Drag and drop the port on the right side of the **Evaluate** block and add an **Output** block.

1. Select **Run**. The **Output** block displays **True**, which means the website is up and running.

## Creating a request and a collection

This is the beginning of a detailed tutorial that builds a flow that gets a list of Pokémon, one page at a time, until it reaches the last page. Start by creating a new collection and adding a GET request. You'll use this collection with the flow you'll create later.

1. In your workspace, select **New &gt; Collection**. Name the collection **Pokemon API**.
1. [Add a GET request](/docs/getting-started/sending-the-first-request/) with this URL: `https://pokeapi.co/api/v2/pokemon?limit=200`.

    ![Add a request](https://assets.postman.com/postman-docs/v10/flow-first-request-v10.jpg)

1. Select **Send**, then select **Save as Example**.

    > Saving the response as an example enables Postman Flows to automatically detect the structure for easier access later.

1. Select the GET request and replace the URL `https://pokeapi.co/api/v2/pokemon?limit=200` with the variable `{{URL}}`.

    ![Replace the URL](https://assets.postman.com/postman-docs/v10/flow-replace-the-url-1-v10.jpg)

1. Select **Save**.

## Making your first send request in Postman Flows

1. Select **New &gt; Flows**. Your new flow appears with a **Start** block already in place.

    > You can select and drag the canvas to reposition your flow.

    ![New flow](https://assets.postman.com/postman-docs/v10/flow-start-block-2-v10.jpg)

1. (Optional) [Hide the sidebar](/docs/getting-started/navigating-postman/#sidebar) to enlarge the canvas.

1. Right-click the canvas to the right of the **Start** block. From the list of blocks that opens, select **Send Request**.

    > You can type the block's name in the **Search** field to find it faster.

1. Connect the **Start** block to the **Send Request** block.

    ![Add Send Request block](https://assets.postman.com/postman-docs/v10/flow-add-send-request-1-v10.jpg)

1. In the **Send Request** block, select **Add request** and select **Pokemon API**. Then select the GET request you created earlier.
    ![Select request](https://assets.postman.com/postman-docs/v10/flow-select-request-1-v10.jpg)

1. Create a **String** block below the **Start** block and enter the URL `https://pokeapi.co/api/v2/pokemon?limit=200`.
1. Connect the **String** block to the port next to `{{URL}}` on the **Send Request** block.

    ![Add a String block](https://assets.postman.com/postman-docs/v10/flow-add-string-block-1-v10.jpg)

## Logging the output

1. Create a **Select** block to the right of the **Send Request** block.
1. Connect the **Select** block to the port next to **Success** on the **Send Request** block.

    ![Add a Select block](https://assets.postman.com/postman-docs/v10/flow-add-select-1-v10.jpg)

1. In the **Select** block, select **Enter path...** and select `body.results`.

    > Because you saved an example earlier, the returned data's structure auto-populates in the block.

    ![Select body.results](https://assets.postman.com/postman-docs/v10/flow-body-results-1-v10.jpg)

1. Create a **Output** block and connect it to the right side of the **Select** block, then select **Run**.
1. View the results.

    ![Add a Log block](https://assets.postman.com/postman-docs/v10/flow-add-log-1-v10.jpg)

## Checking for the next page of results

1. Create another **Select** block and connect it to the **Success** port on the **Send Request** block.

    ![Add another Select block](https://assets.postman.com/postman-docs/v10/flow-add-another-select-1-v10.jpg)

1. In the **Select** block you created, select **Enter path...** and select `body.next` to get the link to the next page of results.

    ![Select `next`](https://assets.postman.com/postman-docs/v10/flow-select-next-v10.jpg)

1. Create an **If** block to the right of the `body.next` **Select** block. Connect the `body.next` **Select** block to the `key` port. This creates a variable named `value1`.

1. Also connect the `body.next` **Select** block to the `Data` port in the **If** block.

    ![Connect the **If** block](https://assets.postman.com/postman-docs/v10/flow-add-if-block-2-v10.jpg)

1. In the **If** block, select `value1` and replace it with `has_next`. This assigns the `body.next` value from the **Select** block to the `has_next` variable in the **If** block.

    ![Enter `has_next`](https://assets.postman.com/postman-docs/v10/flow-enter-has-next-1-v10.jpg)

1. Select **Write an FQL condition** and enter <code class="language-text">&#96;has_next&#96; != null</code>. Or use one of the Code Snippets available.

    > If `has_next` is null, then the flow has reached the last page of results.

1. Connect the **If** block's TRUE port to the **Send Request** block's URL port. This passes the new `has_next` value to the existing `URL` variable in the **Send Request** block.
1. Also connect the **If** block's TRUE port to the **Send Request** block's Send port. This triggers the send event so it runs again.

    ![Connect the If block](https://assets.postman.com/postman-docs/v10/flow-connect-if-2-v10.jpg)

## Watching it run

<!-- vale Postman.Vocab = NO -->

After completing the above steps, select **Run**. The flow runs and logs all the Pokémon to the console.

<!-- vale Postman.Vocab = YES -->

![Watch it run](https://assets.postman.com/postman-docs/v10/flow-watch-it-run-2-v10.gif)
Congratulations, you've created your first flow!
