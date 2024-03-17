 <h2>Hackmap</h2>
  <p>
    This website shows a few million submissions, comments and users of Hacker News.
    The position is determined by an algorithm that places similar titles close to each other.
    The size of the node represents the number of citations.

  </p>
  <p>
    <b>How to use:</b> 
    <ul>
      <li>Use the search box to find an author or a paper</li>
      <li>Use the mouse wheel or two fingers to zoom in and out</li>
    </ul>
    
  </p>
  <p>
      The data was downloaded from the HN-API
      But since ~40 Million items are too much for a browser, 
      I kept only those 2.6 Million with at least some replies.
      I fed the comments to a <a href="https://www.sbert.net/">SentenceTransformers</a> model (all-MiniLM-L6-v2) 
      to create text embeddings. Titles of submissions are often ambiguous, so I used the average embeddings of their comments
      to get a better representation of the content of submissions. The same was done for the users.
      Then I used <a href="https://umap-learn.readthedocs.io/">UMAP</a> to reduce the dimensionality of the embeddings
      to 3, 2 and 1 dimensions. 3 for the colors, 2 for the placement of the nodes and 1 for a plot with the time dimension.
      But the 3D colors didn't add much information, so I removed them. <br/>
      I also used <a href="https://maartengr.github.io/BERTopic/">Bertopic</a> to get clusters and names for these 
      clusters... but they also don't add much information upon the titles of the submissions.

      <br/>
      There are several implementations of maps like this. (todo: add links)
      Some of them are very sophisticated, but they don't show the actual text on the canvas. 
      I think showing as much information as possible, while not overwhelming the user (and browser...)
      is very important for how much the user can get out of such a visualization of big data.
      Another important aspect is that I wanted to host the whole thing on a static hoster,
      which makes things much easier in the long term.
      I used mostly vanilla Javascript (good decision for such a site - no build step 
      and no fighting against Svelte or React) and the excellent 
      <a href="https://github.com/vasturiano/force-graph">force-graph</a> library.

      Since there are too many data points to show at once, the page fetches a base map with
      the 40 000 most important nodes and then fetches additional data tiles when you zoom in.
      Unfortunately, I couldn't find the time to implement a static search over all the data, 
      so the search currently only works for the base-tile of 40 000 nodes.
      <br/>
      The color of the nodes is based on the publication date. The size is based on the 
      score of submissions and the number of direct and indirect child comments for comments 
      and users.
      <br/>


      <br/>

      The biggest challenge in this project was that it worked so well that I got constantly 
      distracted by the stories and comments that I discovered while testing the plot.
      This is why I release it now in this work-in-progress state. Firefox doesn't render some nodes 
      when zoomed in too much, Chrome renders them, but has problems with showing the correct tooltips.
    </p>
    <p>
      Candos and Todos:
      <ul>
        <li>Better search</li>
        <li>More levels of tiles</li>
        <li>Tuning of the size and show parameters</li>
        <li>Earlier data from HN</li>
        <li>Better UI</li>
        <li>Other datasets (MusicBrainz, OpenAlex, Newspapers,...)</li>

      </p>
      If you have any questions or suggestions, please get in touch at <a href="mailto:tom@theilemail.de">tom@theilemail.de</a>
      <p>The code can be found on Github: <a href="https://github.com/tomthe/hackmap">github.com/tomthe/demographymap</a>

      </p>