def get_dataset_from_excel(nlp, path='.', fname='', colname=''):
    import pandas as pd
    if nlp == None:
      nlp = initilize_nlp_model()
    try:
        
        print('reading dataset files (Start)')

        df = pd.read_excel(path + fname)

        dataset = []
        i=1
        for t in tqdm(df[colname]):
            # if i>10:
            #     break
            dataset.append(nlp(t))
            i=i+1

        print('reading dataset files (Done)')
    except:
        raise Exception("get_dataset: reading error.")

    return nlp
