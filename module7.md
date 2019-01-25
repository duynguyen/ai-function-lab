---
layout: module
title: Exercise 3&#58; AI function 1&#58; body crop
---

<!--
# Exercise 3&#58; AI function: body crop
-->

## Overview
In this exercise you will use the **body crop** function to identify reference points in the provided image to use for cropping out the body automatically.

## Steps
1. In Visual Studio Code, open `exercises/exercise-3/composition.js`.
2. Just after the `TODO` block, add the code snippet below to invoke the `/ai-lab/1.0/bodycrop` action. The code will pass in the `image` object and save the result in a `crops` object. The result will contain the constraints recommended for cropping out the body of the image.

        /**
         *  TODO: Use the action '/ai-lab/1.0/bodycrop' to crop the body.
         */
        composer.retain(
            composer.sequence(
                params => ({
                    "image": params.imageObject
                }),
            '/ai-lab/1.0/bodycrop'
            )
        ),
        /* grab bodycrop results */
        ({result, params}) => Object.assign({},
            { crops: result },
            params
        )

## Try it!
1. First, preview your composition to ensure it contains the `bodycrop` action:

       app preview ~/ai-function-lab/exercises/exercise-3/composition.js

    ![](images/exercise3-flow.png)

2. Next update the current `asset_created_composition` app with your new version:

       app update asset_created_composition ~/ai-function-lab/exercises/exercise-3/composition.js

3. Now open the browser to your Creative Cloud folder and upload a new image to trigger an `asset_created` event. For instance, try `image2.png` from the `~/ai-function-lab/stock-photos` folder.

4. Switch back to the **Adobe I/O Runtime Shell** and type:

       session list

5. Locate the most recent `asset_created_composition` running and click on the session id to view the result. The response should contain the coordinates to crop, like shown below:

    ![](images/bodycrop-result.png)


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="module6.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="module8.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>