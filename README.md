# rss-image-downloader

This is a simple script for downloading images from RSS feeds (such as the ones from flickr).

## Usage

    rss-image-download URL DIRECTORY
    rss-image-download DIRECTORY

* `URL`: the RSS feed url, e.g., `http://api.flickr.com/services/feeds/photos_public.gne?tags=interestingness&format=rss_200_enc` (Flickr Interestingness)
    * you need to make sure that there are `<closure>` tags with images
* `DIRECTORY`: the directory to store the images
    * during the first download process the script will save the url as well as the last retrieved rss file inside the directory as well
    * therefore after the first download you only need to supply the `DIRECTORY` argument to retrieve new images
    * the script automatically compares the latest rss feed with the last retrieved one to determine if new images are available for download

## Integration with crontab

For example, I have the following in my crontab

    0 0 * * * find ~/Pictures/wallpapers/'#rss' -type d -links 2 -print0 | xargs -0 -n1 rss-image-download

This updates all my RSS image feeds every day at midnight.
