---
title: "Building News Catcher: A Dynamic News Aggregator Website"
seoTitle: "News Catcher: Building a Dynamic Website"
seoDescription: "Build an Engaging News Aggregator Website with React, Redux, and Newsdata.io AP"
datePublished: Thu Jun 01 2023 02:23:24 GMT+0000 (Coordinated Universal Time)
cuid: clicii71m000008mjhm3mgpkz
slug: building-news-catcher-a-dynamic-news-aggregator-website
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/_Zua2hyvTBk/upload/b9e274118ca2e16e44a21a6078ffc9cd.jpeg
tags: api, reactjs, redux, shivamani

---

Introduction: Welcome to the exciting world of news aggregation! In this blog post, we'll embark on a journey to create News Catcher, a powerful news aggregator website using React, Redux, and the [Newsdata.io](http://Newsdata.io) API. By the end, you'll have a deep understanding of each step involved in building this dynamic platform that brings the latest news right to your fingertips.

Step 1: Setting Up the Foundation To kickstart our News Catcher project, we begin by setting up the basic structure. We import the necessary dependencies, including React, Redux, React Router, and the Bootstrap framework. By utilizing these powerful tools, we ensure our website will be responsive and visually appealing. The code snippet below demonstrates the initial setup:

```javascript
import { Route, Routes } from 'react-router-dom';
import { Layout } from './Layout/Layout';
import { Home } from './Components/Home';

function App() {
  return (
    <div>
      <Layout>
        <Routes>
          <Route path='/' element={<Home />} />
        </Routes>
      </Layout>
    </div>
  );
}

export default App;
```

Step 2: Implementing Redux for State Management To efficiently manage the state of our application, we incorporate Redux. Redux offers a centralized store and enables us to share data across components seamlessly. We define a newsSearchSlice using the `createSlice` function from the `@reduxjs/toolkit` package. This slice represents the initial state and reducers for setting the news data. Take a look at the code snippet below:

```javascript
import { createSlice } from "@reduxjs/toolkit";

const initialState = {
  reduxNews: []
};

export const newsSearchSlice = createSlice({
  name: 'News',
  initialState,
  reducers: {
    setReduxNews: (state, action) => {
      state.reduxNews = action.payload;
    },
  },
});

const { reducer, actions } = newsSearchSlice;
export const { setReduxNews } = actions;
export default reducer;
```

Step 3: Configuring the Redux Store Now that we have our newsSearchSlice, we proceed to configure the Redux store using the `configureStore` function from `@reduxjs/toolkit`. This store serves as the central hub for managing our application's state. In the code snippet below, we set up the store with the `reduxNews` reducer from our newsSearchSlice:

```javascript
import { configureStore } from "@reduxjs/toolkit";
import newsSearchSlice from "./newsSearchSlice";

export const store = configureStore({
  reducer: {
    reduxNews: newsSearchSlice,
  },
});
```

Step 4: Creating Dynamic News Cards To display the news articles in an engaging way, we create a CardHolder component. This component receives the newsData as a prop and renders a Bootstrap Card with relevant information such as the image, title, content, category, and published date. Let's take a closer look at the code snippet for the CardHolder component:

```javascript
import { Button } from 'react-bootstrap';
import Card from 'react-bootstrap/Card';

export const CardHolder = ({ newsData }) => {
  return (
    <>
      <Card className="bg-light d-flex flex-column align-items-center" style={{ minHeight: '200px' }}>
        <Card.Img
          src={newsData?.image_url}
          alt="Card image"
          style={{ maxHeight: '300px' }}
        />
        <Card.Body className="d-flex flex-column align-items-center">
          <Card.Title>{newsData?.title?.slice(0, 50)}</Card.Title>
          <Card.Text>{newsData?.content?.slice(0, 50)}...</Card.Text>
          <Card.Text>Type: {newsData?.category}</Card.Text>
          <Card.Text className="text-primary">Published date: {newsData?.pubDate}</Card.Text>
          <Button variant="primary" href={newsData?.link} target="_blank">Read More</Button>
        </Card.Body>
      </Card>
    </>
  );
};
```

Step 5: Fetching News Data from the API To populate our News Catcher website with the latest news articles, we integrate the [Newsdata.io](http://Newsdata.io) API using Axios. We create a function called `getNews` that makes a GET request to the API, passing the search term and language as query parameters. The response data is returned for further processing. Below is the code snippet for the `getNews` function:

```javascript
import axios from "axios";

export const getNews = async (searchTerm) => {
  try {
    const { data } = await axios.get(`https://newsdata.io/api/1/news?apikey=pub_23191190f4f0567d659bec29740c02ea05abb&q=${searchTerm}&language=en`);
    return data;
  } catch (error) {
    if (error.response) {
      console.log(error.response.status);
      console.log(error.response.headers);
    } else {
      console.log(error.message);
    }
  }
};
```

Conclusion: Congratulations on following along! In this blog post, we explored the step-by-step process of creating News Catcher, a dynamic news aggregator website. We covered setting up the foundation, implementing Redux for state management, configuring the Redux store, creating dynamic news cards, and fetching news data from the [Newsdata.io](http://Newsdata.io) API. By combining the power of React, Redux, and the [Newsdata.io](http://Newsdata.io) API, we built an engaging and user-friendly platform that keeps users informed about the latest news.

Feel free to further enhance your News Catcher website by adding additional features like user authentication, personalized news recommendations, or social sharing options. The possibilities are endless!

Remember to experiment, iterate, and have fun while building your own news aggregator website. Happy coding!