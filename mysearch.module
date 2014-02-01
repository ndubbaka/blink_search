<?php

/**
 * Implementation of hook_permission().
 */
function mysearch_permission() {
  return array(
    'access mysearch' => array(
        'title' => 'Access My Search',
        'description' => 'Allows a user to access search results',
      )
    );
}


/**
 * Implementation of hook_menu().
 */
function mysearch_menu() {
  $items['mysearch'] = array(
    'title' => 'Search',
    'page callback' => 'mysearch_searchpage',
    'access arguments' => array('access mysearch'),
    'type' => MENU_SUGGESTED_ITEM,
  );
  return $items;
}


/**
 * Menu callback provides a simple list of nodes matching the
 * search term Example: hitting the URL:
 *   http://domain.com/mysearch/example
 * will return a list of links to nodes which have the word
 * example in them.
 */
function mysearch_searchpage() {
  $searchterm = arg(1);
  $query = "
     SELECT nid
     FROM node_revisions
     WHERE body LIKE '%$searchterm%'
     ";
  $search_results = db_query($query); 
  $search_results = "<h2>Search for $searchterm</h2><ul>";
  foreach($get_node_result as $record)) {
    $node = node_load($record->nid);
    $search_results .= '<li><a href="/node/'
     . $node->nid . '" title="' . $node->title . '">'
     . $node->title . '</a><!-- debugging output: '
     . print_r($node) . '  --><\li>';
  }
  return $search_results;
}