---
title: Experimenting with Windows Machine Learning and Mixed Reality
date: 2018-05-18T00:27:52+00:00
author: Etienne Margraff
enclosure:
  - |
    http://meulta.com/wp-content/uploads/2018/05/winml.mp4
    6779233
    video/mp4
    
categories:
  - Uncategorized
tags:
  - AI
  - HoloLens
  - Mixed Reality
---
> If you have any question about this blog article, feel free to contact me on twitter: [@meulta](https://twitter.com/meulta)

I have an awesome job at Microsoft: I get to work on mixing AI, Cloud and [Mixed Reality](https://www.microsoft.com/en-us/windows/windows-mixed-reality) experiences with partners and other companies. This enables me to work on cool new stuff and see what companies really want to do. Form all of the Microsoft [Cognitive Services](https://azure.microsoft.com/en-us/services/cognitive-services/) : Computer Vision is one that bring a lot to Augmented reality experiences . We&#8217;ve already helped a lot of companies using the [Custom Vision online service](https://customvision.ai/) which you can access via a REST API. The service tells you what’s in the image by providing a list of tags along with their probability ratio. A new feature was added more recently to show you _where_ these objects are located in the image, thanks to the new Object Detection model with bounding boxes.

The only piece which was missing is offline support. When you don’t have any internet connectivity, these services are not very useful anymore. When detecting that the device you have is offline, you have two possibilities:

  * Disabling the features that require this REST API.
  * Trying to perform object recognition locally, on the device.

We recently announced [Windows Machine Learning](https://docs.microsoft.com/en-us/windows/uwp/machine-learning). It is a service in Windows accessible through a set of APIs when you are building Universal Windows Platform (UWP) applications. This service was released at the end of April 2018 in the brand-new Windows update. The good news is: this Windows update is also available on [HoloLens](https://www.microsoft.com/en-us/hololens)!

This Windows ML feature requires a trained model in the [ONNX format](https://onnx.ai/). ONNX is an initiative from companies such as AWS, Facebook and Microsoft to create an open format to represent deep learning models. One way to create an ONNX model today is to convert it from one that already exists. Guess what? Custom Vision gives you the feature of exporting a trained model in ONNX (for some of the model types available).

I recently worked with a company to try and mix all of this and be able to run a Custom Vision model on HoloLens.

**It worked! Here is how we did it** (using a demo project as an example. You can get the full code here: <https://aka.ms/mr-winml-code>).

<div style="width: 640px;" class="wp-video">
  <video class="wp-video-shortcode" id="video-310-7" width="640" height="200" loop="1" autoplay="1" preload="auto" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2018/05/winml.mp4?_=7" /><a href="http://meulta.com/wp-content/uploads/2018/05/winml.mp4">http://meulta.com/wp-content/uploads/2018/05/winml.mp4</a></video>
</div>

## Use Custom Vision to create an ONNX model

Custom Vision ([customvision.ai](http://www.customvision.ai/)) is one of the Cognitive Services. These are a set of Machine Learning ready-to-use models. The idea is simple: you get the power of Deep Learning and other algorithms without even having to go through the challenge of creating and training the model yourself. If you know how to call a REST API, you know how to use Cognitive Services. Some of these services are customizable. In the Vision API, we have a “Custom” version that you can train by uploading pictures and tagging them.

<p style="text-align: left;">
  <em><strong>Note: </strong>We also recently released a preview of the Object Detection model. It brings you a customizable Vision service WITH bounding boxes! So now not only do you know what is in the picture, you can also know where it is. It is very helpful in Augmented Reality apps as it enables a way to display data on top of objects.</em>
</p>

There is a very comprehensive guide [available here](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier) explaining how to create a classifier so I am not going to go through it here in detail. Here are some interesting things for you to consider:

First, pick a compact model. If you want to export as ONNX, the model as to be marked as **(compact)**, otherwise you won’t be able to. This makes sense in a way that these models are designed to run offline on devices that do not have a lot of power. It is a good way to insure you have usable exported models.

<img class="alignnone wp-image-319" src="http://meulta.com/wp-content/uploads/2018/05/createvisionproject.png" alt="" width="644" height="487" srcset="http://meulta.com/wp-content/uploads/2018/05/createvisionproject.png 1178w, http://meulta.com/wp-content/uploads/2018/05/createvisionproject-300x227.png 300w, http://meulta.com/wp-content/uploads/2018/05/createvisionproject-768x581.png 768w, http://meulta.com/wp-content/uploads/2018/05/createvisionproject-1024x775.png 1024w, http://meulta.com/wp-content/uploads/2018/05/createvisionproject-945x715.png 945w, http://meulta.com/wp-content/uploads/2018/05/createvisionproject-600x454.png 600w" sizes="(max-width: 644px) 100vw, 644px" />

Once you’ve picked the model you need, you just have to train it. In my examples, I am training it using photos of a Rubik’s cube and a Seahawks football (for no particular reason, these were just the first things that I found in my office when writing this sample &#x1f60a; ).

<img class="alignnone wp-image-324" src="http://meulta.com/wp-content/uploads/2018/05/training.png" alt="" width="887" height="489" srcset="http://meulta.com/wp-content/uploads/2018/05/training.png 1690w, http://meulta.com/wp-content/uploads/2018/05/training-300x165.png 300w, http://meulta.com/wp-content/uploads/2018/05/training-768x423.png 768w, http://meulta.com/wp-content/uploads/2018/05/training-1024x564.png 1024w, http://meulta.com/wp-content/uploads/2018/05/training-945x521.png 945w, http://meulta.com/wp-content/uploads/2018/05/training-600x331.png 600w" sizes="(max-width: 887px) 100vw, 887px" />

You can start with as few as 10 pictures for each tag and the service will surprise you with its ability to recognize these very accurately. Of course, you can refine the model by adding more pictures with different lightnings, coloring, etc.

Exporting is very easy, go in the **Performance** tab and click on the **Export** button. You can choose the format you want and in this case, we need ONNX.

<img class="alignnone wp-image-325" src="http://meulta.com/wp-content/uploads/2018/05/export.png" alt="" width="634" height="434" srcset="http://meulta.com/wp-content/uploads/2018/05/export.png 1173w, http://meulta.com/wp-content/uploads/2018/05/export-300x205.png 300w, http://meulta.com/wp-content/uploads/2018/05/export-768x526.png 768w, http://meulta.com/wp-content/uploads/2018/05/export-1024x701.png 1024w, http://meulta.com/wp-content/uploads/2018/05/export-945x647.png 945w, http://meulta.com/wp-content/uploads/2018/05/export-600x411.png 600w" sizes="(max-width: 634px) 100vw, 634px" />

That’s it. We now have a model we can use offline!

## Generate the Windows ML wrapper

Now that we have a model, we need to write some code that is going to make use of it. You can find everything you need about Windows Machine Learning in the [documentation](https://docs.microsoft.com/en-us/windows/uwp/machine-learning/) but let’s get through the main actions you need to perform.

When I say that we need to write some code, it is not completely accurate. We will _generate_ a wrapper to use the ONNX model in UWP. The only code we need to write ourselves is the one that gets the image from the webcam and pass it to the wrapper.

The Windows ML SDK comes with a tool named MLGen.exe. This command line tool helps you generate a wrapper for an ONNX file. It is located where you installed the Windows SDK. On my computer, which has a standard install, here where it is:

<pre>C:\Program Files (x86)\Windows Kits\10\bin\10.0.17125.0\x86\mlgen.exe</pre>

The command line to run is straightforward:

<pre>mlgen -i INPUT-FILE -l LANGUAGE -n NAMESPACE [-o OUTPUT-FILE]</pre>

  * **INPUT-FILE** is the ONNX file.
  * **LANGUAGE** is the programming language (CS in this case).
  * **NAMESPACE** is the namespace used in the CSharp file. This should be something usable in your project, but you can change it later.
  * **OUTPUT-FILE** is the file that is going to be created (a .cs one, in this case).

A generated wrapper contains 3 classes (considering that “ModelName” is the name of your model):

  * **ModelName**_**Input**: a structure to hold the input data. In Vision related model, it is a **VideoFrame** which is easy to get from the Camera in UWP.
  * **ModelName**_**Ouput**: a structure used by the wrapper to give you the output.
  * **ModelName**: a class responsible for running the model evaluation. It contains a static constructor and an asynchronous method to evaluate  the model prediction.

Here is an example of generated code:

<div id="gist89626828" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-wrapper-cs" class="file">
          <div itemprop="text" class="blob-wrapper data type-c ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-wrapper-cs-L1" class="blob-num js-line-number" data-line-number="1">
                </td>
                
                <td id="file-wrapper-cs-LC1" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">using</span> <span class="pl-en">System</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L2" class="blob-num js-line-number" data-line-number="2">
                </td>
                
                <td id="file-wrapper-cs-LC2" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">using</span> <span class="pl-en">System</span>.<span class="pl-en">Collections</span>.<span class="pl-en">Generic</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L3" class="blob-num js-line-number" data-line-number="3">
                </td>
                
                <td id="file-wrapper-cs-LC3" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">using</span> <span class="pl-en">System</span>.<span class="pl-en">Threading</span>.<span class="pl-en">Tasks</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L4" class="blob-num js-line-number" data-line-number="4">
                </td>
                
                <td id="file-wrapper-cs-LC4" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">using</span> <span class="pl-en">Windows</span>.<span class="pl-en">Media</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L5" class="blob-num js-line-number" data-line-number="5">
                </td>
                
                <td id="file-wrapper-cs-LC5" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">using</span> <span class="pl-en">Windows</span>.<span class="pl-en">Storage</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L6" class="blob-num js-line-number" data-line-number="6">
                </td>
                
                <td id="file-wrapper-cs-LC6" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">using</span> <span class="pl-en">Windows</span>.<span class="pl-en">AI</span>.<span class="pl-en">MachineLearning</span>.<span class="pl-en">Preview</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L7" class="blob-num js-line-number" data-line-number="7">
                </td>
                
                <td id="file-wrapper-cs-LC7" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L8" class="blob-num js-line-number" data-line-number="8">
                </td>
                
                <td id="file-wrapper-cs-LC8" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">namespace</span> <span class="pl-en">MyNamespace</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L9" class="blob-num js-line-number" data-line-number="9">
                </td>
                
                <td id="file-wrapper-cs-LC9" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L10" class="blob-num js-line-number" data-line-number="10">
                </td>
                
                <td id="file-wrapper-cs-LC10" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">sealed</span> <span class="pl-k">class</span> <span class="pl-en">MyModelInput</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L11" class="blob-num js-line-number" data-line-number="11">
                </td>
                
                <td id="file-wrapper-cs-LC11" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L12" class="blob-num js-line-number" data-line-number="12">
                </td>
                
                <td id="file-wrapper-cs-LC12" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-en">VideoFrame</span> <span class="pl-smi">data</span> { <span class="pl-k">get</span>; <span class="pl-k">set</span>; }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L13" class="blob-num js-line-number" data-line-number="13">
                </td>
                
                <td id="file-wrapper-cs-LC13" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L14" class="blob-num js-line-number" data-line-number="14">
                </td>
                
                <td id="file-wrapper-cs-LC14" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L15" class="blob-num js-line-number" data-line-number="15">
                </td>
                
                <td id="file-wrapper-cs-LC15" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">sealed</span> <span class="pl-k">class</span> <span class="pl-en">MyModelOutput</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L16" class="blob-num js-line-number" data-line-number="16">
                </td>
                
                <td id="file-wrapper-cs-LC16" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L17" class="blob-num js-line-number" data-line-number="17">
                </td>
                
                <td id="file-wrapper-cs-LC17" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-en">IList</span><<span class="pl-k">string</span>> <span class="pl-smi">classLabel</span> { <span class="pl-k">get</span>; <span class="pl-k">set</span>; }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L18" class="blob-num js-line-number" data-line-number="18">
                </td>
                
                <td id="file-wrapper-cs-LC18" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-en">IDictionary</span><<span class="pl-k">string</span>, <span class="pl-k">float</span>> <span class="pl-smi">loss</span> { <span class="pl-k">get</span>; <span class="pl-k">set</span>; }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L19" class="blob-num js-line-number" data-line-number="19">
                </td>
                
                <td id="file-wrapper-cs-LC19" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-en">MyModelOutput</span>()
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L20" class="blob-num js-line-number" data-line-number="20">
                </td>
                
                <td id="file-wrapper-cs-LC20" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L21" class="blob-num js-line-number" data-line-number="21">
                </td>
                
                <td id="file-wrapper-cs-LC21" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">this</span>.<span class="pl-smi">classLabel</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">List</span><<span class="pl-k">string</span>>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L22" class="blob-num js-line-number" data-line-number="22">
                </td>
                
                <td id="file-wrapper-cs-LC22" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">this</span>.<span class="pl-smi">loss</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">Dictionary</span><<span class="pl-k">string</span>, <span class="pl-k">float</span>>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L23" class="blob-num js-line-number" data-line-number="23">
                </td>
                
                <td id="file-wrapper-cs-LC23" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L24" class="blob-num js-line-number" data-line-number="24">
                </td>
                
                <td id="file-wrapper-cs-LC24" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L25" class="blob-num js-line-number" data-line-number="25">
                </td>
                
                <td id="file-wrapper-cs-LC25" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L26" class="blob-num js-line-number" data-line-number="26">
                </td>
                
                <td id="file-wrapper-cs-LC26" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">sealed</span> <span class="pl-k">class</span> <span class="pl-en">MyModel</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L27" class="blob-num js-line-number" data-line-number="27">
                </td>
                
                <td id="file-wrapper-cs-LC27" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L28" class="blob-num js-line-number" data-line-number="28">
                </td>
                
                <td id="file-wrapper-cs-LC28" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">private</span> <span class="pl-en">LearningModelPreview</span> <span class="pl-smi">learningModel</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L29" class="blob-num js-line-number" data-line-number="29">
                </td>
                
                <td id="file-wrapper-cs-LC29" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">static</span> <span class="pl-k">async</span> <span class="pl-en">Task</span><<span class="pl-en">MyModel</span>> <span class="pl-en">CreateMyModel</span>(<span class="pl-en">StorageFile</span> <span class="pl-smi">file</span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L30" class="blob-num js-line-number" data-line-number="30">
                </td>
                
                <td id="file-wrapper-cs-LC30" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L31" class="blob-num js-line-number" data-line-number="31">
                </td>
                
                <td id="file-wrapper-cs-LC31" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">LearningModelPreview</span> <span class="pl-smi">learningModel</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">LearningModelPreview</span>.<span class="pl-en">LoadModelFromStorageFileAsync</span>(<span class="pl-smi">file</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L32" class="blob-num js-line-number" data-line-number="32">
                </td>
                
                <td id="file-wrapper-cs-LC32" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">MyModel</span> <span class="pl-smi">model</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">MyModel</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L33" class="blob-num js-line-number" data-line-number="33">
                </td>
                
                <td id="file-wrapper-cs-LC33" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">model</span>.<span class="pl-smi">learningModel</span> <span class="pl-k">=</span> <span class="pl-smi">learningModel</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L34" class="blob-num js-line-number" data-line-number="34">
                </td>
                
                <td id="file-wrapper-cs-LC34" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> <span class="pl-smi">model</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L35" class="blob-num js-line-number" data-line-number="35">
                </td>
                
                <td id="file-wrapper-cs-LC35" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L36" class="blob-num js-line-number" data-line-number="36">
                </td>
                
                <td id="file-wrapper-cs-LC36" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">async</span> <span class="pl-en">Task</span><<span class="pl-en">MyModelOutput</span>> <span class="pl-en">EvaluateAsync</span>(<span class="pl-en">MyModelInput</span> <span class="pl-smi">input</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L37" class="blob-num js-line-number" data-line-number="37">
                </td>
                
                <td id="file-wrapper-cs-LC37" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">MyModelOutput</span> <span class="pl-smi">output</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">MyModelOutput</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L38" class="blob-num js-line-number" data-line-number="38">
                </td>
                
                <td id="file-wrapper-cs-LC38" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">LearningModelBindingPreview</span> <span class="pl-smi">binding</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">LearningModelBindingPreview</span>(<span class="pl-smi">learningModel</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L39" class="blob-num js-line-number" data-line-number="39">
                </td>
                
                <td id="file-wrapper-cs-LC39" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">binding</span>.<span class="pl-en">Bind</span>(<span class="pl-s"><span class="pl-pds">"</span>data<span class="pl-pds">"</span></span>, <span class="pl-smi">input</span>.<span class="pl-smi">data</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L40" class="blob-num js-line-number" data-line-number="40">
                </td>
                
                <td id="file-wrapper-cs-LC40" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">binding</span>.<span class="pl-en">Bind</span>(<span class="pl-s"><span class="pl-pds">"</span>classLabel<span class="pl-pds">"</span></span>, <span class="pl-smi">output</span>.<span class="pl-smi">classLabel</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L41" class="blob-num js-line-number" data-line-number="41">
                </td>
                
                <td id="file-wrapper-cs-LC41" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">binding</span>.<span class="pl-en">Bind</span>(<span class="pl-s"><span class="pl-pds">"</span>loss<span class="pl-pds">"</span></span>, <span class="pl-smi">output</span>.<span class="pl-smi">loss</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L42" class="blob-num js-line-number" data-line-number="42">
                </td>
                
                <td id="file-wrapper-cs-LC42" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">LearningModelEvaluationResultPreview</span> <span class="pl-smi">evalResult</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">learningModel</span>.<span class="pl-en">EvaluateAsync</span>(<span class="pl-smi">binding</span>, <span class="pl-smi">string</span>.<span class="pl-smi">Empty</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L43" class="blob-num js-line-number" data-line-number="43">
                </td>
                
                <td id="file-wrapper-cs-LC43" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> <span class="pl-smi">output</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L44" class="blob-num js-line-number" data-line-number="44">
                </td>
                
                <td id="file-wrapper-cs-LC44" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L45" class="blob-num js-line-number" data-line-number="45">
                </td>
                
                <td id="file-wrapper-cs-LC45" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-wrapper-cs-L46" class="blob-num js-line-number" data-line-number="46">
                </td>
                
                <td id="file-wrapper-cs-LC46" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/f4d6c9b8aa69ad76d0ef18dbbfce4fd7/raw/fb1d1dab6d2806c680f25b17ae929d33bc91694a/wrapper.cs" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/f4d6c9b8aa69ad76d0ef18dbbfce4fd7#file-wrapper-cs">wrapper.cs</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

<p style="text-align: left;">
  <em><strong>Note</strong>: When exporting from the Custom Vision service, the name of the model is a generated one. You might have to change it to something that is more human readable.</em>
</p>

As you can see in this example, the generation tool created an output structure with 2 parameters:

  * **classLabel**: the labels with the highest probability.
  * **loss**: a dictionary with all labels and their respective probability.

The dictionary is not initialized. If you leave it this way you will get an Exception when running the code. You have to initialize it using the labels you set in the Custom Vision portal. Here is how it looks like for mine:

<div id="gist89626851" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-vision-cs" class="file">
          <div itemprop="text" class="blob-wrapper data type-c ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-vision-cs-L26" class="blob-num js-line-number" data-line-number="26">
                </td>
                
                <td id="file-vision-cs-LC26" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">this</span>.<span class="pl-smi">loss</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">Dictionary</span><<span class="pl-k">string</span>, <span class="pl-k">float</span>>()
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-vision-cs-L27" class="blob-num js-line-number" data-line-number="27">
                </td>
                
                <td id="file-vision-cs-LC27" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-vision-cs-L28" class="blob-num js-line-number" data-line-number="28">
                </td>
                
                <td id="file-vision-cs-LC28" class="blob-code blob-code-inner js-file-line">
                  { <span class="pl-s"><span class="pl-pds">"</span>football<span class="pl-pds">"</span></span>, <span class="pl-c1">0f</span> },
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-vision-cs-L29" class="blob-num js-line-number" data-line-number="29">
                </td>
                
                <td id="file-vision-cs-LC29" class="blob-code blob-code-inner js-file-line">
                  { <span class="pl-s"><span class="pl-pds">"</span>rubikscube<span class="pl-pds">"</span></span>, <span class="pl-c1">0f</span> }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-vision-cs-L30" class="blob-num js-line-number" data-line-number="30">
                </td>
                
                <td id="file-vision-cs-LC30" class="blob-code blob-code-inner js-file-line">
                  };
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/624304e191630af8aa76d414d3a0ff9a/raw/ab962b534d321ce3987d6dbc27f85c1161f62242/vision.cs" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/624304e191630af8aa76d414d3a0ff9a#file-vision-cs">vision.cs</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

Awesome, we now have a usable wrapper. Let see how we can integrate this in a Mixed Reality app.

## **Integrate in your Mixed Reality app**

The best way to start integrating your wrapper and ONNX model in an application is to look at the [samples](https://docs.microsoft.com/en-us/windows/uwp/machine-learning/samples) that the team is providing. They will guide you through everything you need: starting the Camera, collecting **VideoFrames**, sending these to the wrapper and getting the result.

When you are creating a Windows Mixed Reality application and, more specifically, a HoloLens app, you use Unity to setup your scene with 3D objects as needed along with C# scripts. This Unity project is then built (or “exported”) as a Visual Studio solution containing a Universal Windows Platform (UWP) project.

<p style="text-align: left;">
  <em><strong>Note</strong>: In theory, a Unity project is meant to be exported to different platforms. We usually try to keep the code as portable as possible. In this specific case we are going to use APIs that are specific to Windows to run the evaluation of the ONNX model. To make sure this platform specific code does not generate errors in Unity, we will wrap it inside conditional compilation keyword. This will tell Unity and Visual Studio: “don’t try to parse / compile this unless you are in UWP”. If you want to run this code on another environment you will have to (at least) add another conditional compilation switch to add the code specific to this platform.</em>
</p>

<span style="display: inline !important; float: none; background-color: transparent; color: #333333; cursor: text; font-family: 'Roboto',Helvetica,sans-serif; font-size: 16px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">You can get the full code for this sample here: <a href="https://aka.ms/mr-winml-code">https://aka.ms/mr-winml-code</a> </span>

In the sample project, there is a Game Object with no graphical representation. It is called **ScriptHolder** and its only role is to have some scripts attached to run code at specific moments during execution. This object has a script named **Scene Startup** attached to it. This script contains all the code needed to create the ONNX wrapper, get the **VideoFrames** and display the result of prediction.

The **Start** method in the standard Unity MonoBehaviour is called automatically when the object appears in the scene (i.e. when the application is starting). This will:

  * Get an instance to the label where we are going to display results to.
  * Create and initialize the **MediaCapture** object to start collecting frames from the camera.
  * Initialize the wrapper for the ONNX model.

Initializing the model is pretty easy, you just load the file from the local storage and call the static constructor for the wrapper:

<div id="gist89626875" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-scenestartup-cs" class="file">
          <div itemprop="text" class="blob-wrapper data type-c ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-scenestartup-cs-L45" class="blob-num js-line-number" data-line-number="45">
                </td>
                
                <td id="file-scenestartup-cs-LC45" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">async</span> <span class="pl-k">void</span> <span class="pl-en">InitializeModel</span>()
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L46" class="blob-num js-line-number" data-line-number="46">
                </td>
                
                <td id="file-scenestartup-cs-LC46" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L47" class="blob-num js-line-number" data-line-number="47">
                </td>
                
                <td id="file-scenestartup-cs-LC47" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">StorageFile</span> <span class="pl-smi">imageRecoModelFile</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">StorageFile</span>.<span class="pl-en">GetFileFromApplicationUriAsync</span>(<span class="pl-k">new</span> <span class="pl-en">Uri</span>(<span class="pl-s"><span class="pl-pds">$"</span>ms-appx:///Data/StreamingAssets/model.onnx<span class="pl-pds">"</span></span>));
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L48" class="blob-num js-line-number" data-line-number="48">
                </td>
                
                <td id="file-scenestartup-cs-LC48" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">imageRecoModel</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">Image_RecoModel</span>.<span class="pl-en">CreateImage_RecoModel</span>(<span class="pl-smi">imageRecoModelFile</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L49" class="blob-num js-line-number" data-line-number="49">
                </td>
                
                <td id="file-scenestartup-cs-LC49" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/b5c0c58dd6cf42ed267bcdbe5ca536c8/raw/eb1eb2310c0123bcd13ecc02b9528f2282f729e1/SceneStartup.cs" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/b5c0c58dd6cf42ed267bcdbe5ca536c8#file-scenestartup-cs">SceneStartup.cs</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

To be able to use the ONNX model file in the app, you will need to create a specific folder in Unity called exactly **StreamingAssets** and add the .onnx file there. When you generated the UWP project it will be added in it under _/Data/StreaminAssets_ and its **Build Action** property will be set to **Content**. This way you can access it using the Storage API.

<img class="alignnone wp-image-331" src="http://meulta.com/wp-content/uploads/2018/05/streamingassets.png" alt="" width="483" height="205" srcset="http://meulta.com/wp-content/uploads/2018/05/streamingassets.png 596w, http://meulta.com/wp-content/uploads/2018/05/streamingassets-300x127.png 300w" sizes="(max-width: 483px) 100vw, 483px" />

Initializing the process of getting Video Frames is straightforward. You can take a look at the code in **CreateFrameReader()**. It involves some parameter initialization and a call to the static method: **MediaCapture.CreateFrameReaderAsync**.

Once this is done, we call the **StartPullFrames** method which does all the interesting work.

<div id="gist89626875" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-scenestartup-cs" class="file">
          <div itemprop="text" class="blob-wrapper data type-c ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-scenestartup-cs-L98" class="blob-num js-line-number" data-line-number="98">
                </td>
                
                <td id="file-scenestartup-cs-LC98" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">private</span> <span class="pl-k">void</span> <span class="pl-en">StartPullFrames</span>(<span class="pl-en">MediaFrameReader</span> <span class="pl-smi">sender</span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L99" class="blob-num js-line-number" data-line-number="99">
                </td>
                
                <td id="file-scenestartup-cs-LC99" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L100" class="blob-num js-line-number" data-line-number="100">
                </td>
                
                <td id="file-scenestartup-cs-LC100" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">Task</span>.<span class="pl-en">Run</span>(<span class="pl-k">async</span> () <span class="pl-k">=></span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L101" class="blob-num js-line-number" data-line-number="101">
                </td>
                
                <td id="file-scenestartup-cs-LC101" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L102" class="blob-num js-line-number" data-line-number="102">
                </td>
                
                <td id="file-scenestartup-cs-LC102" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">for</span> (;;)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L103" class="blob-num js-line-number" data-line-number="103">
                </td>
                
                <td id="file-scenestartup-cs-LC103" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L104" class="blob-num js-line-number" data-line-number="104">
                </td>
                
                <td id="file-scenestartup-cs-LC104" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> <span class="pl-smi">frameReference</span> <span class="pl-k">=</span> <span class="pl-smi">sender</span>.<span class="pl-en">TryAcquireLatestFrame</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L105" class="blob-num js-line-number" data-line-number="105">
                </td>
                
                <td id="file-scenestartup-cs-LC105" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> <span class="pl-smi">videoFrame</span> <span class="pl-k">=</span> <span class="pl-smi">frameReference</span><span class="pl-k">?</span>.<span class="pl-smi">VideoMediaFrame</span><span class="pl-k">?</span>.<span class="pl-en">GetVideoFrame</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L106" class="blob-num js-line-number" data-line-number="106">
                </td>
                
                <td id="file-scenestartup-cs-LC106" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (<span class="pl-smi">videoFrame</span> <span class="pl-k">==</span> <span class="pl-c1">null</span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L107" class="blob-num js-line-number" data-line-number="107">
                </td>
                
                <td id="file-scenestartup-cs-LC107" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L108" class="blob-num js-line-number" data-line-number="108">
                </td>
                
                <td id="file-scenestartup-cs-LC108" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">continue</span>; <span class="pl-c"><span class="pl-c">//</span>ignoring frame</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L109" class="blob-num js-line-number" data-line-number="109">
                </td>
                
                <td id="file-scenestartup-cs-LC109" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L110" class="blob-num js-line-number" data-line-number="110">
                </td>
                
                <td id="file-scenestartup-cs-LC110" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> <span class="pl-smi">input</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">Image_RecoModelInput</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L111" class="blob-num js-line-number" data-line-number="111">
                </td>
                
                <td id="file-scenestartup-cs-LC111" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L112" class="blob-num js-line-number" data-line-number="112">
                </td>
                
                <td id="file-scenestartup-cs-LC112" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">input</span>.<span class="pl-smi">data</span> <span class="pl-k">=</span> <span class="pl-smi">videoFrame</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L113" class="blob-num js-line-number" data-line-number="113">
                </td>
                
                <td id="file-scenestartup-cs-LC113" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span>(<span class="pl-smi">videoFrame</span>.<span class="pl-smi">Direct3DSurface</span> <span class="pl-k">==</span> <span class="pl-c1">null</span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L114" class="blob-num js-line-number" data-line-number="114">
                </td>
                
                <td id="file-scenestartup-cs-LC114" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L115" class="blob-num js-line-number" data-line-number="115">
                </td>
                
                <td id="file-scenestartup-cs-LC115" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">continue</span>; <span class="pl-c"><span class="pl-c">//</span>ignoring frame</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L116" class="blob-num js-line-number" data-line-number="116">
                </td>
                
                <td id="file-scenestartup-cs-LC116" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L117" class="blob-num js-line-number" data-line-number="117">
                </td>
                
                <td id="file-scenestartup-cs-LC117" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L118" class="blob-num js-line-number" data-line-number="118">
                </td>
                
                <td id="file-scenestartup-cs-LC118" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">try</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L119" class="blob-num js-line-number" data-line-number="119">
                </td>
                
                <td id="file-scenestartup-cs-LC119" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L120" class="blob-num js-line-number" data-line-number="120">
                </td>
                
                <td id="file-scenestartup-cs-LC120" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">Image_RecoModelOutput</span> <span class="pl-smi">prediction</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">imageRecoModel</span>.<span class="pl-en">EvaluateAsync</span>(<span class="pl-smi">input</span>).<span class="pl-en">ConfigureAwait</span>(<span class="pl-c1">false</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L121" class="blob-num js-line-number" data-line-number="121">
                </td>
                
                <td id="file-scenestartup-cs-LC121" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> <span class="pl-smi">classWithHighestProb</span> <span class="pl-k">=</span> <span class="pl-smi">prediction</span>.<span class="pl-smi">classLabel</span>[<span class="pl-c1"></span>];
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L122" class="blob-num js-line-number" data-line-number="122">
                </td>
                
                <td id="file-scenestartup-cs-LC122" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (<span class="pl-smi">prediction</span>.<span class="pl-smi">loss</span>[<span class="pl-smi">classWithHighestProb</span>] <span class="pl-k">></span> <span class="pl-c1">0.5</span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L123" class="blob-num js-line-number" data-line-number="123">
                </td>
                
                <td id="file-scenestartup-cs-LC123" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L124" class="blob-num js-line-number" data-line-number="124">
                </td>
                
                <td id="file-scenestartup-cs-LC124" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">DisplayText</span>(<span class="pl-s"><span class="pl-pds">"</span>I see a <span class="pl-pds">"</span></span> <span class="pl-k">+</span> <span class="pl-smi">classWithHighestProb</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L125" class="blob-num js-line-number" data-line-number="125">
                </td>
                
                <td id="file-scenestartup-cs-LC125" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L126" class="blob-num js-line-number" data-line-number="126">
                </td>
                
                <td id="file-scenestartup-cs-LC126" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">else</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L127" class="blob-num js-line-number" data-line-number="127">
                </td>
                
                <td id="file-scenestartup-cs-LC127" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L128" class="blob-num js-line-number" data-line-number="128">
                </td>
                
                <td id="file-scenestartup-cs-LC128" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">DisplayText</span>(<span class="pl-s"><span class="pl-pds">"</span>I see nothing<span class="pl-pds">"</span></span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L129" class="blob-num js-line-number" data-line-number="129">
                </td>
                
                <td id="file-scenestartup-cs-LC129" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L130" class="blob-num js-line-number" data-line-number="130">
                </td>
                
                <td id="file-scenestartup-cs-LC130" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L131" class="blob-num js-line-number" data-line-number="131">
                </td>
                
                <td id="file-scenestartup-cs-LC131" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">catch</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L132" class="blob-num js-line-number" data-line-number="132">
                </td>
                
                <td id="file-scenestartup-cs-LC132" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L133" class="blob-num js-line-number" data-line-number="133">
                </td>
                
                <td id="file-scenestartup-cs-LC133" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>Log errors</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L134" class="blob-num js-line-number" data-line-number="134">
                </td>
                
                <td id="file-scenestartup-cs-LC134" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L135" class="blob-num js-line-number" data-line-number="135">
                </td>
                
                <td id="file-scenestartup-cs-LC135" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L136" class="blob-num js-line-number" data-line-number="136">
                </td>
                
                <td id="file-scenestartup-cs-LC136" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">await</span> <span class="pl-smi">Task</span>.<span class="pl-en">Delay</span>(<span class="pl-smi">predictEvery</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L137" class="blob-num js-line-number" data-line-number="137">
                </td>
                
                <td id="file-scenestartup-cs-LC137" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L138" class="blob-num js-line-number" data-line-number="138">
                </td>
                
                <td id="file-scenestartup-cs-LC138" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L139" class="blob-num js-line-number" data-line-number="139">
                </td>
                
                <td id="file-scenestartup-cs-LC139" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L140" class="blob-num js-line-number" data-line-number="140">
                </td>
                
                <td id="file-scenestartup-cs-LC140" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/b5c0c58dd6cf42ed267bcdbe5ca536c8/raw/eb1eb2310c0123bcd13ecc02b9528f2282f729e1/SceneStartup.cs" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/b5c0c58dd6cf42ed267bcdbe5ca536c8#file-scenestartup-cs">SceneStartup.cs</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

_Note: There are a lot of different ways to do this and keep in mind that this is only an example. You should find out the best way to integrate this into your product, which might be different than this approach._

This method starts an infinite loop on a separate thread. This loop tries to get the latest frame that was captured by the camera and after a few tests (is the frame null? Is the **Direct3DSurface** null?) It is given to the **EvaluateAsync** method of the wrapper.

Note that in this case, we ask for it to be run synchronously (with **ConfigureAwait(false)**) so we don’t flood the device with a ton of parallel evaluations.

Once we get the result from the model evaluation, we get the name of the class with the highest probability using **classLabel[0]**. And we check to see if the probability is over 0.5. It is an arbitrary number I picked to not consider detected classes with a too low probability.

If you take a look at the wrapper code in [**Vision.cs**](https://github.com/Microsoft/mixedreality-azure-samples/blob/42289b5c9b49aed5c1e5e6194ad6aa41a66d5ba7/Standalone-Samples/WindowsML-CustomVision-Hololens/Assets/Scripts/Vision.cs#L26), you will notice that the **Input** and **Output** classes are the ones that were generated by the command line tool. The only additions I made were initializing the **Dictionary** with the 2 types of objects available in my custom vision model.

I tried to optimize the **EvaluateAsync** method by pre-initializing objects in the static constructor and only binding the output once. It improved a little bit but not significantly enough to say that this is worth it.

<div id="gist89626875" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-scenestartup-cs" class="file">
          <div itemprop="text" class="blob-wrapper data type-c ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-scenestartup-cs-L34" class="blob-num js-line-number" data-line-number="34">
                </td>
                
                <td id="file-scenestartup-cs-LC34" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">DisplayText</span>(<span class="pl-s"><span class="pl-pds">"</span>Does not work in player.<span class="pl-pds">"</span></span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L35" class="blob-num js-line-number" data-line-number="35">
                </td>
                
                <td id="file-scenestartup-cs-LC35" class="blob-code blob-code-inner js-file-line">
                  #<span class="pl-k">endif</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L36" class="blob-num js-line-number" data-line-number="36">
                </td>
                
                <td id="file-scenestartup-cs-LC36" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L37" class="blob-num js-line-number" data-line-number="37">
                </td>
                
                <td id="file-scenestartup-cs-LC37" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L38" class="blob-num js-line-number" data-line-number="38">
                </td>
                
                <td id="file-scenestartup-cs-LC38" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">private</span> <span class="pl-k">void</span> <span class="pl-en">DisplayText</span>(<span class="pl-k">string</span> <span class="pl-smi">text</span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L39" class="blob-num js-line-number" data-line-number="39">
                </td>
                
                <td id="file-scenestartup-cs-LC39" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L40" class="blob-num js-line-number" data-line-number="40">
                </td>
                
                <td id="file-scenestartup-cs-LC40" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">textToDisplay</span> <span class="pl-k">=</span> <span class="pl-smi">text</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L41" class="blob-num js-line-number" data-line-number="41">
                </td>
                
                <td id="file-scenestartup-cs-LC41" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">textToDisplayChanged</span> <span class="pl-k">=</span> <span class="pl-c1">true</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L42" class="blob-num js-line-number" data-line-number="42">
                </td>
                
                <td id="file-scenestartup-cs-LC42" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L43" class="blob-num js-line-number" data-line-number="43">
                </td>
                
                <td id="file-scenestartup-cs-LC43" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L44" class="blob-num js-line-number" data-line-number="44">
                </td>
                
                <td id="file-scenestartup-cs-LC44" class="blob-code blob-code-inner js-file-line">
                  #<span class="pl-k">if</span> <span class="pl-en">UNITY_WSA</span> <span class="pl-k">&&</span> <span class="pl-k">!</span><span class="pl-en">UNITY_EDITOR</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L45" class="blob-num js-line-number" data-line-number="45">
                </td>
                
                <td id="file-scenestartup-cs-LC45" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">async</span> <span class="pl-k">void</span> <span class="pl-en">InitializeModel</span>()
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L46" class="blob-num js-line-number" data-line-number="46">
                </td>
                
                <td id="file-scenestartup-cs-LC46" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L47" class="blob-num js-line-number" data-line-number="47">
                </td>
                
                <td id="file-scenestartup-cs-LC47" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">StorageFile</span> <span class="pl-smi">imageRecoModelFile</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">StorageFile</span>.<span class="pl-en">GetFileFromApplicationUriAsync</span>(<span class="pl-k">new</span> <span class="pl-en">Uri</span>(<span class="pl-s"><span class="pl-pds">$"</span>ms-appx:///Data/StreamingAssets/model.onnx<span class="pl-pds">"</span></span>));
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L48" class="blob-num js-line-number" data-line-number="48">
                </td>
                
                <td id="file-scenestartup-cs-LC48" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">imageRecoModel</span> <span class="pl-k">=</span> <span class="pl-k">await</span> <span class="pl-smi">Image_RecoModel</span>.<span class="pl-en">CreateImage_RecoModel</span>(<span class="pl-smi">imageRecoModelFile</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L49" class="blob-num js-line-number" data-line-number="49">
                </td>
                
                <td id="file-scenestartup-cs-LC49" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L50" class="blob-num js-line-number" data-line-number="50">
                </td>
                
                <td id="file-scenestartup-cs-LC50" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L51" class="blob-num js-line-number" data-line-number="51">
                </td>
                
                <td id="file-scenestartup-cs-LC51" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">public</span> <span class="pl-k">async</span> <span class="pl-k">void</span> <span class="pl-en">CreateMediaCapture</span>()
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L52" class="blob-num js-line-number" data-line-number="52">
                </td>
                
                <td id="file-scenestartup-cs-LC52" class="blob-code blob-code-inner js-file-line">
                  {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L53" class="blob-num js-line-number" data-line-number="53">
                </td>
                
                <td id="file-scenestartup-cs-LC53" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">MediaCapture</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">MediaCapture</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L54" class="blob-num js-line-number" data-line-number="54">
                </td>
                
                <td id="file-scenestartup-cs-LC54" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">MediaCaptureInitializationSettings</span> <span class="pl-smi">settings</span> <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">MediaCaptureInitializationSettings</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L55" class="blob-num js-line-number" data-line-number="55">
                </td>
                
                <td id="file-scenestartup-cs-LC55" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">settings</span>.<span class="pl-smi">StreamingCaptureMode</span> <span class="pl-k">=</span> <span class="pl-smi">StreamingCaptureMode</span>.<span class="pl-smi">Video</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L56" class="blob-num js-line-number" data-line-number="56">
                </td>
                
                <td id="file-scenestartup-cs-LC56" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">await</span> <span class="pl-smi">MediaCapture</span>.<span class="pl-en">InitializeAsync</span>(<span class="pl-smi">settings</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L57" class="blob-num js-line-number" data-line-number="57">
                </td>
                
                <td id="file-scenestartup-cs-LC57" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L58" class="blob-num js-line-number" data-line-number="58">
                </td>
                
                <td id="file-scenestartup-cs-LC58" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">CreateFrameReader</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-scenestartup-cs-L59" class="blob-num js-line-number" data-line-number="59">
                </td>
                
                <td id="file-scenestartup-cs-LC59" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/b5c0c58dd6cf42ed267bcdbe5ca536c8/raw/eb1eb2310c0123bcd13ecc02b9528f2282f729e1/SceneStartup.cs" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/b5c0c58dd6cf42ed267bcdbe5ca536c8#file-scenestartup-cs">SceneStartup.cs</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

That’s it! Only a few lines of code using an out of the box feature from Windows and you get an offline Custom Vision model on HoloLens.

## Moving forward

Running this on a HoloLens is pretty fun: you look at a football, it says “I see a football” then you look at a Rubik’s cube and it says that is it a Rubik’s cube. Ok… maybe it is not the most exciting app but I can tell you that this will help a lot of developers handling offline scenarios! 🙂

Windows Machine Learning is still new and in preview. We can expect that this will improve a lot in the future. When using a Machine that supports it, Windows ML uses the GPU to do model evaluation. Keep in mind that on HoloLens, it’s only using the CPU.  This means that you must be very cautious about what model you use on this kind of device. Whether it’s a HoloLens, a phone or a tablet, you’ll want to test it and make sure it is fast enough for your scenario. A good idea might be to use the [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) to understand usage of the CPU and the GPU in your app. Right now, I have no idea if using the GPU will ever be possible on HoloLens for this kind of processing.

Deep Learning and tools from this big AI family are really the next frontier for AR and VR. In the coming years they are going to be the key component to evolve from good apps to magical experiences.

## **Credits**

Huge thanks to [Jason Fox](https://twitter.com/JasonGFox), [Jared Bienz](https://twitter.com/jbienz), [Nick Landry](https://twitter.com/ActiveNick) and [Simon Ferquel](https://twitter.com/sferquel) for the help on reviewing this article and the sample code.

> If you have any question about this blog article, feel free to contact me on twitter: [@meulta](https://twitter.com/meulta)

&nbsp;