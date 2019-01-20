# cms
content management
<nav class="navbar navbar-expand-sm navbar-dark bg-dark p-3">
  <a class="navbar-brand" href="#">CmsJutsu</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navMenu" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navMenu">
    <ul class="navbar-nav">
      <?php $results_cats=get_all_categories();?>
      <?php while($category_row=mysqli_fetch_assoc($results_cats)) {?>
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#"  id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
<?php echo $category_row["cat_name"]; ?>
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          
          <?php $results_pages_of=get_pages_of($category_row["id"]);
          while($page_row=mysqli_fetch_assoc($results_pages_of)){ ?>
            <?php
            echo "<a ";
            if($current_page && $current_page["id"]==$page_row["id"]){
                echo "class=\"dropdown-item active\" ";
            }else{
                echo "class=\"dropdown-item\" ";
            }

            echo "href=\"index.php?page={$page_row["id"]}\">";
            echo "{$page_row["page_name"]} ";
            echo "</a>";
            ?>
        <?php } //end of pages while?>
        </div>
      </li>
<?php } //end of category while ?>
<?php mysqli_free_result($results_cats);?>
    </ul>

  </div>
</nav>
