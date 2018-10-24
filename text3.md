n <- power.t.test(power = 0.9, delta = .01, sd = .04, type = "one.sample", alt = "one.sided")$n
n
ceiling(n/10)*10

check_data <- function(x){
        columns = c("title", "readers", "suggested","minimum")
        if(ncol(x)!=4) {
                stop('Your spreadsheet does not have four columns. Please go back to your Google Sheet and make sure you have four columns: "title", "readers", "suggested", and "minimum". Then, re-run all the code.')
        }
        if(!(identical(colnames(x),tolower(colnames(x))))) {
                stop('Your column names should all be lowercase. Please go back to your Google Sheet and make sure your column headers are "title", "readers", "suggested", and "minimum". Then, re-run all the code.')
        }
        if(!(all(colnames(df) %in% columns))) {
                stop('Your column names are not what was expected. Please go back to your Google Sheet and make sure your column headers are "title", "readers", "suggested", and "minimum". Then, re-run all the code.')
        }
        if(nrow(x)<10) {
                stop('Your spreadsheet should contain data from at least 10 books. Please go back to your Google Sheet and make sure you have entered data from at least 10 books with one book in each row. Then, re-run all the code.')
        }
        if(length(grep("[\\$]",unlist(df)))>0) {
                stop('Your spreadsheet should not have dollar signs. Please go back to your Google Sheet and remove the dollar signs from your spreadsheet. Then, re-run all the code.')
        }
        "Your spreadsheet has passed all checks. You're ready to plot!"
}

check_link <- function(x){
        if(grepl("edit",x)) {
                stop('You have not yet removed the end of the Google Sheet link. Return to leanpub course and double check instructions to remove the last part of the copied link')
        }
}

