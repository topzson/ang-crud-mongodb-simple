<h1>Angular 15 + Node.js + MongoDB example: CRUD App</h1>

<div class="entry-content">
<p>In this tutorial, I will show you how to make Angular 15 connect to MongoDB with Node.js Express. We’re gonna build a full-stack Angular 15 + Node.js Express + MongoDB example (MEAN stack CRUD) in which, the back-end server uses Node.js + Express for REST APIs, front-end side is an Angular App with HttpClient, Router and Bootstrap.</p>
<p>Other versions:<br>
– <a href="https://www.bezkoder.com/angular-mongodb-node-express/">Using Angular 8</a><br>
– <a href="https://www.bezkoder.com/angular-10-mongodb-node-express/">Using Angular 10</a><br>
– <a href="https://www.bezkoder.com/angular-11-mongodb-node-js-express/">Using Angular 11</a><br>
– <a href="https://www.bezkoder.com/angular-12-mongodb-node-js-express/">Using Angular 12</a><br>
– <a href="https://www.bezkoder.com/mean-stack-crud-example-angular-13/">Using Angular 13</a><br>
– <a href="https://www.bezkoder.com/mean-stack-crud-example-angular-14/">Using Angular 14</a></p>
<p>Run both projects in one place:<br>
<a href="https://bezkoder.com/integrate-angular-12-node-js/">How to Integrate Angular with Node.js Restful Services</a></p>
<p>Security: <a href="https://www.bezkoder.com/mean-stack-auth-angular-15/">MEAN stack Authentication &amp; Authorization example</a><br>
Serverless with Firebase:<br>
– <a href="https://www.bezkoder.com/angular-15-firebase-crud/">Angular 15 Firebase CRUD example with Realtime DB</a><br>
– <a href="https://www.bezkoder.com/angular-15-firestore-crud/">Angular 15 Firestore CRUD example</a></p>
<p><span id="more-13681"></span><br>
</p><div id="toc_container" class="no_bullets"><p class="toc_title">Contents <span class="toc_toggle">[<a href="#">hide</a>]</span></p><ul class="toc_list"><li><a href="#Angular_15_Nodejs_MongoDB_Overview">Angular 15 + Nodejs + MongoDB Overview</a></li><li><a href="#Angular_15_Nodejs_MongoDB_Architecture">Angular 15 + Node.js + MongoDB Architecture</a></li><li><a href="#Video">Video</a></li><li><a href="#Nodejs_Express_MongoDB_Back-end">Node.js Express MongoDB Back-end</a><ul><li><a href="#Overview">Overview</a></li><li><a href="#Project_Structure">Project Structure</a></li><li><a href="#Create_Nodejs_App">Create Node.js App</a></li><li><a href="#Setup_Express_web_server">Setup Express web server</a></li><li><a href="#Configure_MongoDB_database_038_Mongoose">Configure MongoDB database &amp; Mongoose</a></li><li><a href="#Define_Mongoose">Define Mongoose</a></li><li><a href="#Define_the_Mongoose_Model">Define the Mongoose Model</a></li><li><a href="#Create_the_Controller">Create the Controller</a></li><li><a href="#Run_the_Nodejs_Server">Run the Nodejs Server</a></li></ul></li><li><a href="#Angular_15_Front-end">Angular 15 Front-end</a><ul><li><a href="#Overview-2">Overview</a></li><li><a href="#Technology">Technology</a></li><li><a href="#Project_Structure-2">Project Structure</a></li><li><a href="#Setup_Angular_15_Project">Setup Angular 15 Project</a></li><li><a href="#Set_up_App_Module">Set up App Module</a></li><li><a href="#Define_Routes_for_Angular_AppRoutingModule">Define Routes for Angular AppRoutingModule</a></li><li><a href="#Define_Model_Class">Define Model Class</a></li><li><a href="#Create_Data_Service">Create Data Service</a></li><li><a href="#Create_Angular_15_Components">Create Angular 15 Components</a></li><li><a href="#Run_the_Angular_15_App">Run the Angular 15 App</a></li></ul></li><li><a href="#Further_Reading">Further Reading</a></li><li><a href="#Source_Code">Source Code</a></li><li><a href="#Conclusion">Conclusion</a></li></ul></div>
<p></p>
<h2><span id="Angular_15_Nodejs_MongoDB_Overview">Angular 15 + Nodejs + MongoDB Overview</span></h2>
<p>We will build a MEAN stack CRUD example: Angular 15 + Nodejs Express + MongoDB Tutorial Application in that:</p>
<ul>
<li>Tutorial has id, title, description, published status.</li>
<li>User can create, retrieve, update, delete Tutorials.</li>
<li>There is a search box for finding Tutorials by title.</li>
</ul>
<p>Here are screenshots of the example.</p>
<p>– Create a Tutorial document:</p>

<div class="quads-location quads-ad1" id="quads-ad1" style="float: left; margin: 15px 15px 15px 0px; visibility: visible;">
<div class="aicp" style="float:none;margin:30px 0 30px 0;text-align:center;">
<div style="float:left;margin-right:15px;">
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" type="text/javascript"></script>

<ins class="adsbygoogle" style="display:inline-block;width:300px;height:250px" data-ad-client="ca-pub-9222145312954144" data-ad-slot="9066284388"><iframe id="aswift_0" style="height: 1px !important; max-height: 1px !important; max-width: 1px !important; width: 1px !important;"><iframe id="google_ads_frame0"></iframe></iframe></ins>
<script type="text/javascript">
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>
</div>
<div style="float:left;">
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" type="text/javascript"></script>

<ins class="adsbygoogle" style="display:inline-block;width:300px;height:250px" data-ad-client="ca-pub-9222145312954144" data-ad-slot="1209584201"><iframe id="aswift_1" style="height: 1px !important; max-height: 1px !important; max-width: 1px !important; width: 1px !important;"><iframe id="google_ads_frame1"></iframe></iframe></ins>
<script type="text/javascript">
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>
</div>
</div>
</div>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create.png" alt="mean-stack-crud-example-angular-15-tutorial-create" width="570" height="340" class="alignnone size-full wp-image-13706 ls-is-cached lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create.png 570w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create-300x179.png 300w" sizes="(max-width: 570px) 100vw, 570px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create.png 570w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create-300x179.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create.png" alt="mean-stack-crud-example-angular-15-tutorial-create" width="570" height="340" class="alignnone size-full wp-image-13706 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create.png 570w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-create-300x179.png 300w" sizes="(max-width: 570px) 100vw, 570px" /></noscript></p>
<p>– Retrieve all Tutorial documents:</p>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve.png" alt="mean-stack-crud-example-angular-15-tutorial-retrieve" width="700" height="500" class="alignnone size-full wp-image-13707 ls-is-cached lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve.png 700w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-300x214.png 300w" sizes="(max-width: 700px) 100vw, 700px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve.png 700w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-300x214.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve.png" alt="mean-stack-crud-example-angular-15-tutorial-retrieve" width="700" height="500" class="alignnone size-full wp-image-13707 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve.png 700w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-300x214.png 300w" sizes="(max-width: 700px) 100vw, 700px" /></noscript></p>
<p>– Click on <strong>Edit</strong> button to update a document:</p>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one.png" alt="mean-stack-crud-example-angular-15-tutorial-retrieve-one" width="600" height="400" class="alignnone size-full wp-image-13708 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one.png 600w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one-300x200.png 300w" sizes="(max-width: 600px) 100vw, 600px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one.png 600w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one-300x200.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one.png" alt="mean-stack-crud-example-angular-15-tutorial-retrieve-one" width="600" height="400" class="alignnone size-full wp-image-13708 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one.png 600w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-retrieve-one-300x200.png 300w" sizes="(max-width: 600px) 100vw, 600px" /></noscript></p>
<p>On this Page, you can:</p>
<ul>
<li>change status to <strong>Published</strong> using <strong>Publish</strong> button</li>
<li>delete the Tutorial using <strong>Delete</strong> button</li>
<li>update the Tutorial details with <strong>Update</strong> button</li>
</ul>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update.png" alt="mean-stack-crud-example-angular-15-tutorial-update" width="450" height="340" class="alignnone size-full wp-image-13709 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update.png 450w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update-300x227.png 300w" sizes="(max-width: 450px) 100vw, 450px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update.png 450w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update-300x227.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update.png" alt="mean-stack-crud-example-angular-15-tutorial-update" width="450" height="340" class="alignnone size-full wp-image-13709 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update.png 450w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-update-300x227.png 300w" sizes="(max-width: 450px) 100vw, 450px" /></noscript></p>

<div class="quads-location quads-ad2" id="quads-ad2" style="float: none; margin: 30px 0px; text-align: center; visibility: visible;">
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" type="text/javascript"></script>
<ins class="adsbygoogle" style="display:block; text-align:center;" data-ad-layout="in-article" data-ad-format="fluid" data-ad-client="ca-pub-9222145312954144" data-ad-slot="8580577265"><iframe id="aswift_2" style="height: 1px !important; max-height: 1px !important; max-width: 1px !important; width: 1px !important;"><iframe id="google_ads_frame2"></iframe></iframe></ins>
<script type="text/javascript">
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>
</div>
<p>If you want to implement Form Validation, please visit:</p>
<ul>
<li><a href="https://www.bezkoder.com/angular-15-form-validation/">Angular 15 Reactive Form Validation example</a></li>
<li><a href="https://www.bezkoder.com/angular-15-template-driven-form-validation/">Angular 15 Template Driven Form Validation example</a></li>
</ul>
<p>– Search Tutorials by title:</p>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search.png" alt="mean-stack-crud-example-angular-15-tutorial-search" width="710" height="300" class="alignnone size-full wp-image-13710 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search.png 710w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search-300x127.png 300w" sizes="(max-width: 710px) 100vw, 710px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search.png 710w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search-300x127.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search.png" alt="mean-stack-crud-example-angular-15-tutorial-search" width="710" height="300" class="alignnone size-full wp-image-13710 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search.png 710w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-tutorial-search-300x127.png 300w" sizes="(max-width: 710px) 100vw, 710px" /></noscript></p>
<p>– Check MongoDB Database:</p>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection.png" alt="mean-stack-crud-example-angular-15-database-collection" width="810" height="390" class="alignnone size-full wp-image-13711 ls-is-cached lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection.png 810w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection-300x144.png 300w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection-768x370.png 768w" sizes="(max-width: 810px) 100vw, 810px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection.png 810w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection-300x144.png 300w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection-768x370.png 768w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection.png" alt="mean-stack-crud-example-angular-15-database-collection" width="810" height="390" class="alignnone size-full wp-image-13711 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection.png 810w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection-300x144.png 300w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-database-collection-768x370.png 768w" sizes="(max-width: 810px) 100vw, 810px" /></noscript></p>

<div class="quads-location quads-ad3" id="quads-ad3" style="float: none; margin: 30px 0px; text-align: center; visibility: visible;">
<div class="aicp">
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" type="text/javascript"></script>
<ins class="adsbygoogle" style="display:block; text-align:center;" data-ad-layout="in-article" data-ad-format="fluid" data-ad-client="ca-pub-9222145312954144" data-ad-slot="4842295194"><iframe id="aswift_3" style="height: 1px !important; max-height: 1px !important; max-width: 1px !important; width: 1px !important;"><iframe id="google_ads_frame3"></iframe></iframe></ins>
<script type="text/javascript">
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>
</div>
</div>
<h2><span id="Angular_15_Nodejs_MongoDB_Architecture">Angular 15 + Node.js + MongoDB Architecture</span></h2>
<p>We’re gonna build the MEAN stack – Angular 15 + Node Express + MongoDb application with following architecture:</p>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture.png" alt="mean-stack-crud-example-angular-15-architecture" width="692" height="255" class="alignnone size-full wp-image-13712 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture.png 692w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture-300x111.png 300w" sizes="(max-width: 692px) 100vw, 692px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture.png 692w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture-300x111.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture.png" alt="mean-stack-crud-example-angular-15-architecture" width="692" height="255" class="alignnone size-full wp-image-13712 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture.png 692w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-architecture-300x111.png 300w" sizes="(max-width: 692px) 100vw, 692px" /></noscript></p>
<p>– Node.js Express exports REST APIs &amp; interacts with MongoDB Database using Mongoose ODM.<br>
– Angular 15 Client sends HTTP Requests and retrieves HTTP Responses using <em>HTTPClient</em>, consume data on the components. Angular Router is used for navigating to pages.</p>
<h2><span id="Video">Video</span></h2>
<p>This is brief instruction and demo for Angular + Node.js Express application running with MongoDB database.</p>
<p><iframe class=" lazyloaded" width="853" height="480" data-src="https://www.youtube.com/embed/LXErOsejHdc?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" src="https://www.youtube.com/embed/LXErOsejHdc?rel=0"></iframe></p>
<p>In the video, we use Angular 10, but the logic and UI are the same as this Angular version 15.</p>
<h2><span id="Nodejs_Express_MongoDB_Back-end">Node.js Express MongoDB Back-end</span></h2>
<h3><span id="Overview">Overview</span></h3>
<p>These are APIs that Node.js Express App will export:</p>
<div class="table-responsive">
<table class="table table-hover  table table-hover table table-hover" width="100%">
<thead>
<tr>
<th>Methods</th>
<th>Urls</th>
<th>Actions</th>
</tr>
</thead>
<tbody>
<tr>
<td>GET</td>
<td>api/tutorials</td>
<td>get all Tutorials</td>
</tr>
<tr>
<td>GET</td>
<td>api/tutorials/:id</td>
<td>get Tutorial by <code>id</code></td>
</tr>
<tr>
<td>POST</td>
<td>api/tutorials</td>
<td>add new Tutorial</td>
</tr>
<tr>
<td>PUT</td>
<td>api/tutorials/:id</td>
<td>update Tutorial by <code>id</code></td>
</tr>
<tr>
<td>DELETE</td>
<td>api/tutorials/:id</td>
<td>remove Tutorial by <code>id</code></td>
</tr>
<tr>
<td>DELETE</td>
<td>api/tutorials</td>
<td>remove all Tutorials</td>
</tr>
<tr>
<td>GET</td>
<td>api/tutorials?title=[kw]</td>
<td>find all Tutorials which title contains <code>'kw'</code></td>
</tr>
</tbody>
</table>
</div>
<h3><span id="Project_Structure">Project Structure</span></h3>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project.png" alt="mean-stack-crud-example-angular-15-server-project" width="180" height="330" class="alignnone size-full wp-image-13713 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project.png 180w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project-164x300.png 164w" sizes="(max-width: 180px) 100vw, 180px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project.png 180w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project-164x300.png 164w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project.png" alt="mean-stack-crud-example-angular-15-server-project" width="180" height="330" class="alignnone size-full wp-image-13713 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project.png 180w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-project-164x300.png 164w" sizes="(max-width: 180px) 100vw, 180px" /></noscript></p>
<p>– <em>db.config.js</em> exports configuring parameters for MongoDB connection &amp; Mongoose.<br>
– <strong>Express</strong> web server in <em>server.js</em> where we configure CORS, initialize &amp; run Express REST APIs.<br>
– Next, we add configuration for MongoDB database in <strong>models</strong>/<em>index.js</em>, create <strong>Mongoose</strong> data model in <strong>models</strong>/<em>tutorial.model.js</em>.<br>
– Tutorial controller in <strong>controllers</strong>.<br>
– Routes for handling all CRUD operations (including custom finder) in <em>tutorial.routes.js</em>.</p>
<h3><span id="Create_Nodejs_App">Create Node.js App</span></h3>
<p>First, we create a folder:</p>
<pre><code>$ mkdir nodejs-express-mongodb
$ cd nodejs-express-mongodb
</code></pre>
<p>Next, we initialize the Node.js App with a <em>package.json</em> file:</p>
<pre><code>npm init

name: (nodejs-express-mongodb) 
version: (1.0.0) 
description: Node.js Restful CRUD API with Node.js, Express and MongoDB
entry point: (index.js) server.js
test command: 
git repository: 
keywords: nodejs, express, mongodb, rest, api
author: bezkoder
license: (ISC)

Is this ok? (yes) yes
</code></pre>
<p>We need to install necessary modules: <code>express</code>, <code>mongoose</code> and <code>cors</code>.<br>
Run the command:</p>
<pre><code>npm install express mongoose cors --save
</code></pre>
<h3><span id="Setup_Express_web_server">Setup Express web server</span></h3>
<p>In the root folder, let’s create a new <em>server.js</em> file:</p>
<pre class=" language-js"><code class=" language-js"><span class="token keyword">const</span> express <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"express"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> cors <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"cors"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token function">express</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">var</span> corsOptions <span class="token operator">=</span> <span class="token punctuation">{</span>
  origin<span class="token operator">:</span> <span class="token string">"http://localhost:8081"</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token method function property-access">use</span><span class="token punctuation">(</span><span class="token function">cors</span><span class="token punctuation">(</span>corsOptions<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// parse requests of content-type - application/json</span>
app<span class="token punctuation">.</span><span class="token method function property-access">use</span><span class="token punctuation">(</span>express<span class="token punctuation">.</span><span class="token method function property-access">json</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// parse requests of content-type - application/x-www-form-urlencoded</span>
app<span class="token punctuation">.</span><span class="token method function property-access">use</span><span class="token punctuation">(</span>express<span class="token punctuation">.</span><span class="token method function property-access">urlencoded</span><span class="token punctuation">(</span><span class="token punctuation">{</span> extended<span class="token operator">:</span> <span class="token boolean">true</span> <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// simple route</span>
app<span class="token punctuation">.</span><span class="token method function property-access">get</span><span class="token punctuation">(</span><span class="token string">"/"</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  res<span class="token punctuation">.</span><span class="token method function property-access">json</span><span class="token punctuation">(</span><span class="token punctuation">{</span> message<span class="token operator">:</span> <span class="token string">"Welcome to bezkoder application."</span> <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// set port, listen for requests</span>
<span class="token keyword">const</span> <span class="token constant">PORT</span> <span class="token operator">=</span> process<span class="token punctuation">.</span><span class="token property-access">env</span><span class="token punctuation">.</span><span class="token constant">PORT</span> <span class="token operator">||</span> <span class="token number">8080</span><span class="token punctuation">;</span>
app<span class="token punctuation">.</span><span class="token method function property-access">listen</span><span class="token punctuation">(</span><span class="token constant">PORT</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  <span class="token console class-name">console</span><span class="token punctuation">.</span><span class="token method function property-access">log</span><span class="token punctuation">(</span><span class="token template-string"><span class="token template-punctuation string">`</span><span class="token string">Server is running on port </span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span><span class="token constant">PORT</span><span class="token interpolation-punctuation punctuation">}</span></span><span class="token string">.</span><span class="token template-punctuation string">`</span></span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>What we do are:<br>
– import <code>express</code> and <code>cors</code> modules:</p>
<ul>
<li>Express is for building the Rest apis</li>
<li><a href="https://www.npmjs.com/package/cors">cors</a> provides Express middleware to enable CORS with various options.</li>
</ul>
<p>– create an Express app, then add body-parser (<code>json</code> and <code>urlencoded</code>) and <code>cors</code> middlewares using <code>app.use()</code> method. Notice that we set origin: <code>http://localhost:8081</code>.<br>
– define a GET route which is simple for test.<br>
– listen on port 8080 for incoming requests.</p>
<p>Now let’s run the app with command: <code>node server.js</code>.<br>
Open your browser with url <a href="http://localhost:8080/">http://localhost:8080/</a>, you will see:</p>
<p><img decoding="async" src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-setup.png" alt="mean-stack-crud-example-angular-15-server-setup" width="394" height="144" class="alignnone size-full wp-image-13714 lazyload" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-setup.png 394w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-setup-300x110.png 300w" sizes="(max-width: 394px) 100vw, 394px"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-setup.png" alt="mean-stack-crud-example-angular-15-server-setup" width="394" height="144" class="alignnone size-full wp-image-13714 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-setup.png 394w, https://www.bezkoder.com/wp-content/uploads/mean-stack-crud-example-angular-15-server-setup-300x110.png 300w" sizes="(max-width: 394px) 100vw, 394px" /></noscript></p>
<p>Yeah, the first step is done. We’re gonna work with Mongoose in the next section.</p>
<h3><span id="Configure_MongoDB_database_038_Mongoose">Configure MongoDB database &amp; Mongoose</span></h3>
<p>In the <em>app</em> folder, we create a separate <em>config</em> folder for configuration with <em>db.config.js</em> file like this:</p>
<pre class=" language-js"><code class=" language-js">module<span class="token punctuation">.</span><span class="token property-access">exports</span> <span class="token operator">=</span> <span class="token punctuation">{</span>
  url<span class="token operator">:</span> <span class="token string">"mongodb://localhost:27017/bezkoder_db"</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<h3><span id="Define_Mongoose">Define Mongoose</span></h3>
<p>We’re gonna define Mongoose model (<em>tutorial.model.js</em>) also in <strong>app</strong>/<strong>models</strong> folder in the next step.</p>
<p>Now create <strong>app</strong>/<strong>models</strong>/<em>index.js</em> with the following code:</p>
<pre class=" language-js"><code class=" language-js"><span class="token keyword">const</span> dbConfig <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"../config/db.config.js"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> mongoose <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"mongoose"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
mongoose<span class="token punctuation">.</span><span class="token known-class-name class-name">Promise</span> <span class="token operator">=</span> global<span class="token punctuation">.</span><span class="token known-class-name class-name">Promise</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> db <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token punctuation">}</span><span class="token punctuation">;</span>
db<span class="token punctuation">.</span><span class="token property-access">mongoose</span> <span class="token operator">=</span> mongoose<span class="token punctuation">;</span>
db<span class="token punctuation">.</span><span class="token property-access">url</span> <span class="token operator">=</span> dbConfig<span class="token punctuation">.</span><span class="token property-access">url</span><span class="token punctuation">;</span>
db<span class="token punctuation">.</span><span class="token property-access">tutorials</span> <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"./tutorial.model.js"</span><span class="token punctuation">)</span><span class="token punctuation">(</span>mongoose<span class="token punctuation">)</span><span class="token punctuation">;</span>

module<span class="token punctuation">.</span><span class="token property-access">exports</span> <span class="token operator">=</span> db<span class="token punctuation">;</span>
</code></pre>
<p>Don’t forget to call <code>connect()</code> method in <em>server.js</em>:</p>
<pre class=" language-js"><code class=" language-js"><span class="token spread operator">...</span>
<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token function">express</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
app<span class="token punctuation">.</span><span class="token method function property-access">use</span><span class="token punctuation">(</span><span class="token spread operator">...</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> db <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"./app/models"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
db<span class="token punctuation">.</span><span class="token property-access">mongoose</span>
  <span class="token punctuation">.</span><span class="token method function property-access">connect</span><span class="token punctuation">(</span>db<span class="token punctuation">.</span><span class="token property-access">url</span><span class="token punctuation">,</span> <span class="token punctuation">{</span>
    useNewUrlParser<span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span>
    useUnifiedTopology<span class="token operator">:</span> <span class="token boolean">true</span>
  <span class="token punctuation">}</span><span class="token punctuation">)</span>
  <span class="token punctuation">.</span><span class="token method function property-access">then</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
    <span class="token console class-name">console</span><span class="token punctuation">.</span><span class="token method function property-access">log</span><span class="token punctuation">(</span><span class="token string">"Connected to the database!"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">)</span>
  <span class="token punctuation">.</span><span class="token method function property-access">catch</span><span class="token punctuation">(</span><span class="token parameter">err</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
    <span class="token console class-name">console</span><span class="token punctuation">.</span><span class="token method function property-access">log</span><span class="token punctuation">(</span><span class="token string">"Cannot connect to the database!"</span><span class="token punctuation">,</span> err<span class="token punctuation">)</span><span class="token punctuation">;</span>
    process<span class="token punctuation">.</span><span class="token method function property-access">exit</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h3><span id="Define_the_Mongoose_Model">Define the Mongoose Model</span></h3>
<p>In <em>models</em> folder, create <em>tutorial.model.js</em> file like this:</p>
<pre class=" language-js"><code class=" language-js">module<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">exports</span> <span class="token operator">=</span> <span class="token parameter">mongoose</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  <span class="token keyword">const</span> <span class="token maybe-class-name">Tutorial</span> <span class="token operator">=</span> mongoose<span class="token punctuation">.</span><span class="token method function property-access">model</span><span class="token punctuation">(</span>
    <span class="token string">"tutorial"</span><span class="token punctuation">,</span>
    mongoose<span class="token punctuation">.</span><span class="token method function property-access"><span class="token maybe-class-name">Schema</span></span><span class="token punctuation">(</span>
      <span class="token punctuation">{</span>
        title<span class="token operator">:</span> <span class="token known-class-name class-name">String</span><span class="token punctuation">,</span>
        description<span class="token operator">:</span> <span class="token known-class-name class-name">String</span><span class="token punctuation">,</span>
        published<span class="token operator">:</span> <span class="token known-class-name class-name">Boolean</span>
      <span class="token punctuation">}</span><span class="token punctuation">,</span>
      <span class="token punctuation">{</span> timestamps<span class="token operator">:</span> <span class="token boolean">true</span> <span class="token punctuation">}</span>
    <span class="token punctuation">)</span>
  <span class="token punctuation">)</span><span class="token punctuation">;</span>

  <span class="token keyword">return</span> <span class="token maybe-class-name">Tutorial</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<p>This Mongoose Model represents <strong>tutorials</strong> collection in MongoDB database. These fields will be generated automatically for each Tutorial document: <em>_id</em>, <em>title</em>, <em>description</em>, <em>published</em>, <em>createdAt</em>, <em>updatedAt</em>, <em>__v</em>.</p>
<pre class=" language-json"><code class=" language-json"><span class="token punctuation">{</span>
  <span class="token property">"_id"</span><span class="token operator">:</span> <span class="token string">"5e363b135036a835ac1a7da8"</span><span class="token punctuation">,</span>
  <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"Js Tut#"</span><span class="token punctuation">,</span>
  <span class="token property">"description"</span><span class="token operator">:</span> <span class="token string">"Description for Tut#"</span><span class="token punctuation">,</span>
  <span class="token property">"published"</span><span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span>
  <span class="token property">"createdAt"</span><span class="token operator">:</span> <span class="token string">"2022-12-22T02:59:31.198Z"</span><span class="token punctuation">,</span>
  <span class="token property">"updatedAt"</span><span class="token operator">:</span> <span class="token string">"2022-12-22T02:59:31.198Z"</span><span class="token punctuation">,</span>
  <span class="token property">"__v"</span><span class="token operator">:</span> <span class="token number">0</span>
<span class="token punctuation">}</span>
</code></pre>
<p>If you use this app with a front-end that needs <em>id</em> field instead of <em>_id</em>, you have to override <code>toJSON</code> method that map default object to a custom object. So the Mongoose model could be modified as following code:</p>
<pre class=" language-js"><code class=" language-js">module<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">exports</span> <span class="token operator">=</span> <span class="token parameter">mongoose</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  <span class="token keyword">var</span> schema <span class="token operator">=</span> mongoose<span class="token punctuation">.</span><span class="token method function property-access"><span class="token maybe-class-name">Schema</span></span><span class="token punctuation">(</span>
    <span class="token punctuation">{</span>
      title<span class="token operator">:</span> <span class="token known-class-name class-name">String</span><span class="token punctuation">,</span>
      description<span class="token operator">:</span> <span class="token known-class-name class-name">String</span><span class="token punctuation">,</span>
      published<span class="token operator">:</span> <span class="token known-class-name class-name">Boolean</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span> timestamps<span class="token operator">:</span> <span class="token boolean">true</span> <span class="token punctuation">}</span>
  <span class="token punctuation">)</span><span class="token punctuation">;</span>

  schema<span class="token punctuation">.</span><span class="token method function property-access">method</span><span class="token punctuation">(</span><span class="token string">"toJSON"</span><span class="token punctuation">,</span> <span class="token keyword">function</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">const</span> <span class="token punctuation">{</span> __v<span class="token punctuation">,</span> _id<span class="token punctuation">,</span> <span class="token spread operator">...</span>object <span class="token punctuation">}</span> <span class="token operator">=</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token method function property-access">toObject</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    object<span class="token punctuation">.</span><span class="token property-access">id</span> <span class="token operator">=</span> _id<span class="token punctuation">;</span>
    <span class="token keyword">return</span> object<span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

  <span class="token keyword">const</span> <span class="token maybe-class-name">Tutorial</span> <span class="token operator">=</span> mongoose<span class="token punctuation">.</span><span class="token method function property-access">model</span><span class="token punctuation">(</span><span class="token string">"tutorial"</span><span class="token punctuation">,</span> schema<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">return</span> <span class="token maybe-class-name">Tutorial</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<p>And the result will look like this-</p>
<pre class=" language-json"><code class=" language-json"><span class="token punctuation">{</span>
  <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"BezKoder Tut#"</span><span class="token punctuation">,</span>
  <span class="token property">"description"</span><span class="token operator">:</span> <span class="token string">"Description for Tut#"</span><span class="token punctuation">,</span>
  <span class="token property">"published"</span><span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span>
  <span class="token property">"createdAt"</span><span class="token operator">:</span> <span class="token string">"2022-12-22T02:59:31.198Z"</span><span class="token punctuation">,</span>
  <span class="token property">"updatedAt"</span><span class="token operator">:</span> <span class="token string">"2022-12-22T02:59:31.198Z"</span><span class="token punctuation">,</span>
  <span class="token property">"id"</span><span class="token operator">:</span> <span class="token string">"5e363b135036a835ac1a7da8"</span>
<span class="token punctuation">}</span>
</code></pre>
<p>After finishing the steps above, we don’t need to write CRUD functions, Mongoose Model supports all of them:</p>
<ul>
<li>create a new Tutorial: object.<a href="https://mongoosejs.com/docs/api/model.html#model_Model-save">save()</a></li>
<li>find a Tutorial by id: <a href="https://mongoosejs.com/docs/api/model.html#model_Model.findById">findById</a>(id)</li>
<li>retrieve all Tutorials: <a href="https://mongoosejs.com/docs/api/model.html#model_Model.find">find()</a></li>
<li>update a Tutorial by id: <a href="https://mongoosejs.com/docs/api/model.html#model_Model.findByIdAndUpdate">findByIdAndUpdate</a>(id, data)</li>
<li>remove a Tutorial: <a href="https://mongoosejs.com/docs/api/model.html#model_Model.findByIdAndRemove">findByIdAndRemove</a>(id)</li>
<li>remove all Tutorials: <a href="https://mongoosejs.com/docs/api/model.html#model_Model.deleteMany">deleteMany()</a></li>
<li>find all Tutorials by title: find({ title: { $regex: new RegExp(title), $options: “i” } })</li>

</ul>
<p>These functions will be used in our Controller.</p>
<h3><span id="Create_the_Controller">Create the Controller</span></h3>
<p>Inside <strong>app</strong>/<strong>controllers</strong> folder, let’s create <em>tutorial.controller.js</em> with these CRUD functions:</p>
<ul>
<li>create</li>
<li>findAll</li>
<li>findOne</li>
<li>update</li>
<li>delete</li>
<li>deleteAll</li>
<li>findAllPublished</li>
</ul>
<pre class=" language-js"><code class=" language-js"><span class="token keyword">const</span> db <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"../models"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> <span class="token maybe-class-name">Tutorial</span> <span class="token operator">=</span> db<span class="token punctuation">.</span><span class="token property-access">tutorials</span><span class="token punctuation">;</span>

<span class="token comment">// Create and Save a new Tutorial</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">create</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>

<span class="token comment">// Retrieve all Tutorials from the database.</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">findAll</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>

<span class="token comment">// Find a single Tutorial with an id</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">findOne</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>

<span class="token comment">// Update a Tutorial by the id in the request</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">update</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>

<span class="token comment">// Delete a Tutorial with the specified id in the request</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">delete</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>

<span class="token comment">// Delete all Tutorials from the database.</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">deleteAll</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>

<span class="token comment">// Find all published Tutorials</span>
exports<span class="token punctuation">.</span><span class="token method-variable function-variable method function property-access">findAllPublished</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token parameter">req<span class="token punctuation">,</span> res</span><span class="token punctuation">)</span> <span class="token arrow operator">=&gt;</span> <span class="token punctuation">{</span>
  
<span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<p>You can continue with step by step to implement this Node.js Express App in the post:<br>
<a href="https://bezkoder.com/node-express-mongodb-crud-rest-api/">Node.js, Express &amp; MongoDb: Build a CRUD Rest Api example</a></p>
<h3><span id="Run_the_Nodejs_Server">Run the Nodejs Server</span></h3>
<p>Run our Node.js Express MongoDB application with command: <code>node server.js</code>.</p>
<h2><span id="Angular_15_Front-end">Angular 15 Front-end</span></h2>
<h3><span id="Overview-2">Overview</span></h3>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview.png" alt="mean-stack-example-crud-angular-15-overview" width="700" height="208" class="alignnone size-full wp-image-13715 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview.png 700w, https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview-300x89.png 300w" sizes="(max-width: 700px) 100vw, 700px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview.png 700w, https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview-300x89.png 300w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview.png" alt="mean-stack-example-crud-angular-15-overview" width="700" height="208" class="alignnone size-full wp-image-13715 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview.png 700w, https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-overview-300x89.png 300w" sizes="(max-width: 700px) 100vw, 700px" /></noscript></p>
<p>– The <code>App</code> component is a container with <code>router-outlet</code>. It has navbar that links to routes paths via <code>routerLink</code>.</p>
<p>– <code>TutorialsList</code> component gets and displays Tutorials.<br>
– <code>TutorialDetails</code> component has form for editing Tutorial’s details based on <code>:id</code>.<br>
– <code>AddTutorial</code> component has form for submission new Tutorial.</p>
<p>– These Components call <code>TutorialService</code> methods which use Angular <code>HTTPClient</code> to make HTTP requests and receive responses.</p>
<h3><span id="Technology">Technology</span></h3>
<ul>
<li>Angular 15</li>
<li>Angular HttpClient</li>
<li>Angular Router</li>
<li>Bootstrap 4</li>
</ul>
<h3><span id="Project_Structure-2">Project Structure</span></h3>
<p><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project.png" data-src="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project.png" alt="mean-stack-example-crud-angular-15-project" width="210" height="690" class="alignnone size-full wp-image-13716 ls-is-cached lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project.png 210w, https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project-91x300.png 91w" sizes="(max-width: 210px) 100vw, 210px" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project.png 210w, https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project-91x300.png 91w"><noscript><img decoding="async" src="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project.png" alt="mean-stack-example-crud-angular-15-project" width="210" height="690" class="alignnone size-full wp-image-13716 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project.png 210w, https://www.bezkoder.com/wp-content/uploads/mean-stack-example-crud-angular-15-project-91x300.png 91w" sizes="(max-width: 210px) 100vw, 210px" /></noscript></p>
<p>– <code>tutorial.model.ts</code> exports the main class model: <code>Tutorial</code>.<br>
– There are 3 components: <code>tutorials-list</code>, <code>tutorial-details</code>, <code>add-tutorial</code>.<br>
– <code>tutorial.service</code> has methods for sending HTTP requests to the Apis.<br>
– <strong>app-routing.module.ts</strong> defines routes for each component.<br>
– <code>app</code> component contains router view and navigation bar.<br>
– <code>app.module.ts</code> declares Angular components and import necessary modules.</p>
<h3><span id="Setup_Angular_15_Project">Setup Angular 15 Project</span></h3>
<p>Let’s open cmd and use Angular CLI to create a new Angular Project as following command:</p>
<pre class=" language-bash"><code class=" language-bash">ng new angular-15-crud-example
? Would you like to add Angular routing? Yes
? Which stylesheet format would you like to use? CSS
</code></pre>
<p>We also need to generate some Components and Services:</p>
<pre class=" language-bash"><code class=" language-bash">ng g s services/tutorial

ng g c components/add-tutorial
ng g c components/tutorial-details
ng g c components/tutorials-list

ng g class models/tutorial --type=model
</code></pre>
<h3><span id="Set_up_App_Module">Set up App Module</span></h3>
<p>Open <em>app.module.ts</em> and import <code>FormsModule</code>, <code>HttpClientModule</code>:</p>
<pre class=" language-js"><code class=" language-js"><span class="token spread operator">...</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">FormsModule</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'@angular/forms'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">HttpClientModule</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'@angular/common/http'</span><span class="token punctuation">;</span>

@<span class="token function"><span class="token maybe-class-name">NgModule</span></span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  declarations<span class="token operator">:</span> <span class="token punctuation">[</span> <span class="token spread operator">...</span> <span class="token punctuation">]</span><span class="token punctuation">,</span>
  imports<span class="token operator">:</span> <span class="token punctuation">[</span>
    <span class="token spread operator">...</span>
    <span class="token maybe-class-name">FormsModule</span><span class="token punctuation">,</span>
    <span class="token maybe-class-name">HttpClientModule</span>
  <span class="token punctuation">]</span><span class="token punctuation">,</span>
  providers<span class="token operator">:</span> <span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
  bootstrap<span class="token operator">:</span> <span class="token punctuation">[</span><span class="token maybe-class-name">AppComponent</span><span class="token punctuation">]</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword module">export</span> <span class="token keyword">class</span> <span class="token class-name">AppModule</span> <span class="token punctuation">{</span> <span class="token punctuation">}</span>
</code></pre>
<h3><span id="Define_Routes_for_Angular_AppRoutingModule">Define Routes for Angular AppRoutingModule</span></h3>
<p>There are 3 main routes:<br>
– <code>/tutorials</code> for <code>tutorials-list</code> component<br>
– <code>/tutorials/:id</code> for <code>tutorial-details</code> component<br>
– <code>/add</code> for <code>add-tutorial</code> component</p>
<p><em>app-routing.module.ts</em></p>
<pre class=" language-js"><code class=" language-js"><span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">NgModule</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">RouterModule</span><span class="token punctuation">,</span> <span class="token maybe-class-name">Routes</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'@angular/router'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">TutorialsListComponent</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'./components/tutorials-list/tutorials-list.component'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">TutorialDetailsComponent</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'./components/tutorial-details/tutorial-details.component'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">AddTutorialComponent</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'./components/add-tutorial/add-tutorial.component'</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> routes<span class="token operator">:</span> <span class="token maybe-class-name">Routes</span> <span class="token operator">=</span> <span class="token punctuation">[</span>
  <span class="token punctuation">{</span> path<span class="token operator">:</span> <span class="token string">''</span><span class="token punctuation">,</span> redirectTo<span class="token operator">:</span> <span class="token string">'tutorials'</span><span class="token punctuation">,</span> pathMatch<span class="token operator">:</span> <span class="token string">'full'</span> <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span> path<span class="token operator">:</span> <span class="token string">'tutorials'</span><span class="token punctuation">,</span> component<span class="token operator">:</span> <span class="token maybe-class-name">TutorialsListComponent</span> <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span> path<span class="token operator">:</span> <span class="token string">'tutorials/:id'</span><span class="token punctuation">,</span> component<span class="token operator">:</span> <span class="token maybe-class-name">TutorialDetailsComponent</span> <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span> path<span class="token operator">:</span> <span class="token string">'add'</span><span class="token punctuation">,</span> component<span class="token operator">:</span> <span class="token maybe-class-name">AddTutorialComponent</span> <span class="token punctuation">}</span>
<span class="token punctuation">]</span><span class="token punctuation">;</span>

@<span class="token function"><span class="token maybe-class-name">NgModule</span></span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  imports<span class="token operator">:</span> <span class="token punctuation">[</span><span class="token maybe-class-name">RouterModule</span><span class="token punctuation">.</span><span class="token method function property-access">forRoot</span><span class="token punctuation">(</span>routes<span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
  exports<span class="token operator">:</span> <span class="token punctuation">[</span><span class="token maybe-class-name">RouterModule</span><span class="token punctuation">]</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword module">export</span> <span class="token keyword">class</span> <span class="token class-name">AppRoutingModule</span> <span class="token punctuation">{</span> <span class="token punctuation">}</span>
</code></pre>
<h3><span id="Define_Model_Class">Define Model Class</span></h3>
<p>Our main model class <code>Tutorial</code> will be exported in <em>tutorial.model.ts</em> with 4 fields:</p>
<ul>
<li><code>id</code></li>
<li><code>title</code></li>
<li><code>description</code></li>
<li><code>published</code></li>
</ul>
<p><strong>models</strong>/<em>tutorial.model.ts</em></p>
<pre class=" language-js"><code class=" language-js"><span class="token keyword module">export</span> <span class="token keyword">class</span> <span class="token class-name">Tutorial</span> <span class="token punctuation">{</span>
  id<span class="token operator">?</span><span class="token operator">:</span> any<span class="token punctuation">;</span>
  title<span class="token operator">?</span><span class="token operator">:</span> string<span class="token punctuation">;</span>
  description<span class="token operator">?</span><span class="token operator">:</span> string<span class="token punctuation">;</span>
  published<span class="token operator">?</span><span class="token operator">:</span> boolean<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h3><span id="Create_Data_Service">Create Data Service</span></h3>
<p>This service will use Angular <code>HttpClient</code> to send HTTP requests.<br>
You can see that its functions includes CRUD operations and finder method.</p>
<p><strong>services</strong>/<em>tutorial.service.ts</em></p>
<pre class=" language-js"><code class=" language-js"><span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">Injectable</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'@angular/core'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">HttpClient</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'@angular/common/http'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">Observable</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'rxjs'</span><span class="token punctuation">;</span>
<span class="token keyword module">import</span> <span class="token punctuation">{</span> <span class="token maybe-class-name">Tutorial</span> <span class="token punctuation">}</span> <span class="token keyword module">from</span> <span class="token string">'../models/tutorial.model'</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> baseUrl <span class="token operator">=</span> <span class="token string">'http://localhost:8080/api/tutorials'</span><span class="token punctuation">;</span>

@<span class="token function"><span class="token maybe-class-name">Injectable</span></span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  providedIn<span class="token operator">:</span> <span class="token string">'root'</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token keyword module">export</span> <span class="token keyword">class</span> <span class="token class-name">TutorialService</span> <span class="token punctuation">{</span>

  <span class="token function">constructor</span><span class="token punctuation">(</span><span class="token parameter"><span class="token keyword">private</span> http<span class="token operator">:</span> <span class="token maybe-class-name">HttpClient</span></span><span class="token punctuation">)</span> <span class="token punctuation">{</span> <span class="token punctuation">}</span>

  <span class="token function">getAll</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span><span class="token maybe-class-name">Tutorial</span><span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token property-access">get</span><span class="token operator">&lt;</span><span class="token maybe-class-name">Tutorial</span><span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token operator">&gt;</span><span class="token punctuation">(</span>baseUrl<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token keyword">get</span><span class="token punctuation">(</span>id<span class="token operator">:</span> any<span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span><span class="token maybe-class-name">Tutorial</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token method function property-access">get</span><span class="token punctuation">(</span><span class="token template-string"><span class="token template-punctuation string">`</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>baseUrl<span class="token interpolation-punctuation punctuation">}</span></span><span class="token string">/</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>id<span class="token interpolation-punctuation punctuation">}</span></span><span class="token template-punctuation string">`</span></span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">create</span><span class="token punctuation">(</span>data<span class="token operator">:</span> any<span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span>any<span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token method function property-access">post</span><span class="token punctuation">(</span>baseUrl<span class="token punctuation">,</span> data<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">update</span><span class="token punctuation">(</span>id<span class="token operator">:</span> any<span class="token punctuation">,</span> data<span class="token operator">:</span> any<span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span>any<span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token method function property-access">put</span><span class="token punctuation">(</span><span class="token template-string"><span class="token template-punctuation string">`</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>baseUrl<span class="token interpolation-punctuation punctuation">}</span></span><span class="token string">/</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>id<span class="token interpolation-punctuation punctuation">}</span></span><span class="token template-punctuation string">`</span></span><span class="token punctuation">,</span> data<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token keyword">delete</span><span class="token punctuation">(</span>id<span class="token operator">:</span> any<span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span>any<span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token method function property-access">delete</span><span class="token punctuation">(</span><span class="token template-string"><span class="token template-punctuation string">`</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>baseUrl<span class="token interpolation-punctuation punctuation">}</span></span><span class="token string">/</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>id<span class="token interpolation-punctuation punctuation">}</span></span><span class="token template-punctuation string">`</span></span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">deleteAll</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span>any<span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token method function property-access">delete</span><span class="token punctuation">(</span>baseUrl<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">findByTitle</span><span class="token punctuation">(</span>title<span class="token operator">:</span> any<span class="token punctuation">)</span><span class="token operator">:</span> <span class="token maybe-class-name">Observable</span><span class="token operator">&lt;</span><span class="token maybe-class-name">Tutorial</span><span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token property-access">http</span><span class="token punctuation">.</span><span class="token property-access">get</span><span class="token operator">&lt;</span><span class="token maybe-class-name">Tutorial</span><span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token operator">&gt;</span><span class="token punctuation">(</span><span class="token template-string"><span class="token template-punctuation string">`</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>baseUrl<span class="token interpolation-punctuation punctuation">}</span></span><span class="token string">?title=</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>title<span class="token interpolation-punctuation punctuation">}</span></span><span class="token template-punctuation string">`</span></span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h3><span id="Create_Angular_15_Components">Create Angular 15 Components</span></h3>
<p>As you’ve known before, there are 3 components corresponding to 3 routes defined in <code>AppRoutingModule</code>.</p>
<ul>
<li>Add new Item Component</li>
<li>List of items Component</li>
<li>Item details Component</li>
</ul>
<p>You can continue with step by step to implement this Angular App in the post:<br>
<a href="https://www.bezkoder.com/angular-15-crud-example/">Angular 15 CRUD example with Web API</a></p>
<h3><span id="Run_the_Angular_15_App">Run the Angular 15 App</span></h3>
<p>You can run this App with command: <code>ng serve --port 8081</code>.<br>
If the process is successful, open Browser with Url: <code>http://localhost:8081/</code> and check it.</p>
<h2><span id="Further_Reading">Further Reading</span></h2>
<ul>
<li><a href="http://expressjs.com/en/guide/routing.html">Express.js Routing</a></li>
<li><a href="https://www.npmjs.com/package/express">https://www.npmjs.com/package/express</a></li>
<li><a href="https://www.npmjs.com/package/mongoose">https://www.npmjs.com/package/mongoose</a></li>
<li><a href="https://mongoosejs.com/docs/guide.html">https://mongoosejs.com/docs/guide.html</a></li>
<li><a href="https://angular.io/guide/http">Angular HttpClient</a></li>
<li><a href="https://angular.io/guide/template-syntax">Angular Template Syntax</a></li>
</ul>
<h2><span id="Source_Code">Source Code</span></h2>
<p>You can find source code for this tutorial at: <a href="https://github.com/bezkoder/angular-15-node-js-mongodb-example">Angular Node.js MongoDB example GitHub</a></p>
<h2><span id="Conclusion">Conclusion</span></h2>
<p>Now we have an overview of how to make Angular 15 + Nodejs + MongoDB example with Express Rest API when building a MEAN stack CRUD example.</p>
<p>We also take a look at client-server architecture for REST API using Express &amp; Mongoose ODM, as well as Angular 15 project structure for building a front-end app to make HTTP requests and consume responses.</p>
<p>Next tutorials show you more details about how to implement the system (with Github):<br>
– <a href="https://www.bezkoder.com/node-express-mongodb-crud-rest-api/">Back-end</a><br>
– Front-end:</p>
<ul>
<li><a href="https://www.bezkoder.com/angular-crud-app/">Using Angular 8</a></li>
<li><a href="https://www.bezkoder.com/angular-10-crud-app/">Using Angular 10</a></li>
<li><a href="https://www.bezkoder.com/angular-11-crud-app/">Using Angular 11</a></li>
<li><a href="https://www.bezkoder.com/angular-12-crud-app/">Using Angular 12</a></li>
<li><a href="https://www.bezkoder.com/angular-13-crud-example/">Using Angular 13</a></li>
<li><a href="https://www.bezkoder.com/angular-14-crud-example/">Using Angular 14</a></li>
<li><a href="https://www.bezkoder.com/angular-15-crud-example/">Using Angular 15</a></li>
</ul>
<p>You will want to know how to run both projects in one place:<br>
<a href="https://bezkoder.com/integrate-angular-12-node-js/">How to Integrate Angular with Node.js Restful Services</a></p>
<p>Or <a href="https://www.bezkoder.com/angular-15-node-express-file-upload/">File Upload using Angular and Node.js</a></p>
<p>Pagination: <a href="https://bezkoder.com/server-side-pagination-node-js-angular/">Server side Pagination with Node.js and Angular</a></p>
<p><img decoding="async" src="https://bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size.png" data-src="https://bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size.png" alt="server-side-pagination-node-js-angular-ui-change-size" width="660" height="610" class="alignnone size-full wp-image-4841 lazyloaded" data-srcset="https://www.bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size.png 660w, https://www.bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size-300x277.png 300w" sizes="(max-width: 660px) 100vw, 660px" srcset="https://www.bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size.png 660w, https://www.bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size-300x277.png 300w"><noscript><img decoding="async" src="https://bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size.png" alt="server-side-pagination-node-js-angular-ui-change-size" width="660" height="610" class="alignnone size-full wp-image-4841 lazyload" srcset="https://www.bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size.png 660w, https://www.bezkoder.com/wp-content/uploads/2020/10/server-side-pagination-node-js-angular-ui-change-size-300x277.png 300w" sizes="(max-width: 660px) 100vw, 660px" /></noscript></p>
<p>Security: <a href="https://www.bezkoder.com/mean-stack-auth-angular-15/">MEAN stack Authentication &amp; Authorization example</a></p>
<p>Or Serverless with Firebase:<br>
– <a href="https://www.bezkoder.com/angular-15-firebase-crud/">Angular 15 Firebase CRUD example with Realtime DB</a><br>
– <a href="https://www.bezkoder.com/angular-15-firestore-crud/">Angular 15 Firestore CRUD example</a></p>
<p>If you want to implement Form Validation, please visit:</p>
<ul>
<li><a href="https://www.bezkoder.com/angular-15-form-validation/">Angular 15 Reactive Form Validation example</a></li>
<li><a href="https://www.bezkoder.com/angular-15-template-driven-form-validation/">Angular 15 Template Driven Form Validation example</a></li>
</ul>

<div class="quads-location quads-ad4" id="quads-ad4" style="float: none; margin: 20px 0px; text-align: center; visibility: visible;">

</div>


</div>
