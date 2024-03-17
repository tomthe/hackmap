 <h2>Demographic research map</h2>
  <p>
    This plot shows a few thousand of the most important authors and papers from some important demographic journals.
    The position is determined by an algorithm that places similar titles close to each other.
    The size of the node represents the number of citations.

  </p>
  <p>
    <b>How to use:</b> 
    <ul>
      <!-- <li>Click on a node to see the author's name and the number of works and citations</li> -->
      <!-- <li>Click on the author's name to open the author's page on <a href="https://www.demographic-research.org/">Demographic Research</a></li> -->
      <li>Use the search box to find an author or a paper</li>
      <li>Use the mouse wheel or two fingers to zoom in and out</li>
    </ul>
    
  </p>
  <details>
    <summary>Details</summary>
    <p>
      The data was downloaded from <a href="https://openalex.org/works?sort=cited_by_count%3Adesc&column=display_name,publication_year,type,open_access.is_oa,cited_by_count&page=1&filter=primary_location.source.id%3AS184793761%7CS30543418%7CS32314625%7CS202512192%7CS79946630%7CS4210206495%7CS190460170%7CS3035070908">Open Alex</a> on 2024-01-08.
      I included all articles from the journals 
      <a href="https://www.demographic-research.org/">Demographic Research</a>,
      <a href="https://read.dukeupress.edu/demography">Demography</a>, 
      <a href="https://www.tandfonline.com/journals/rpst20">Population Studies</a>,
      <a href="https://onlinelibrary.wiley.com/journal/17284457">Population and Development Review</a>,
      <a href="#">Population and Policy Review</a>,
      <a href="#">Population</a>,
      <a href="#">Population space and place</a>,
      <a href="#">European Journal of Population</a>,
      <a href="#">Population Studies</a> and
      <a href="#">Genus</a>.
      But since 30 thousand authors and 40 thousand papers are too much for a browser, 
      I kept only 4500 authors and 4000 papers, based on their last publication year and the number of citations.
      
    </p>
    <p>
      I used <a href="https://www.sbert.net/">SentenceTransformers</a> and the model
       <a href="https://huggingface.co/thenlper/gte-small">thenlper/gte-small</a>
      to create text embeddings of the titles of the articles.
      Text embeddings are vectors with hundreds or thousands (in this case 384) of dimensions that 
      represent the meaning of a text. Similar texts have similar embeddings.
      Then I used <a href="https://umap-learn.readthedocs.io/">UMAP</a> to reduce the 
      dimensionality of the embeddings to 2 dimensions. 
      The placement of the articles in the plot is based on these 2 dimensions, 
      no citation information is used for the placement.
      For the authors I averaged the embeddings of all their articles and then used the same UMAP model again.
      <br/>
      The size of the nodes is based on the number of citations.
      <br/>
      The color of the nodes is based on the year of the last publication.
      <br/>
      I used the Javascript library <a href="https://github.com/vasturiano/force-graph">force-graph</a>
      to paint the nodes on the canvas.
      But I had to optimize the painting a bit so that nodes outside of the visible 
      area are not painted and the text is only painted if you zoom in enough.
      <br/>
      The inspiration came from a 
      <a href="https://bsky.app/profile/ikashnitsky.phd/post/3khedvmcu4y23">social media post</a>
      by Ilya Kashnitsky which plots the 50 most prolific authors in demography. Why limit us to 50 when we can show 4500?

      </p>
      If you have any questions or suggestions, please get in touch at <a href="mailto:theile@mpidr.de">theile@mpidr.de</a>
      <p>The code can be found on Github: <a href="https://github.com/tomthe/demographymap">github.com/tomthe/demographymap</a>

      </p>
  </details>
  